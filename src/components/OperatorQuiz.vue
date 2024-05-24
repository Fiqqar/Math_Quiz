<template>
    <div>
        <div v-if="isQuizStarted">
            <h4>{{ operandLeft }} {{ operator }} {{ operandRight }}</h4>
            <button 
            v-for="(answer, index) in answers" 
            :key="index"
            @click="selectAnswer(answer)">
            {{ answer }}</button>
        </div>
        <div v-if="!isQuizStarted">
            <button @click="startQuiz">Start</button>
            
        </div>
        <button @click="$emit('onBack')">Back</button>
    </div>
</template>
<script>
export default {
    props: ["operator"],
    data () {
        return {
            operandLeft: null,
            operandRight: null,
            isQuizStarted: false,
            answers: [],
            expectedAnswer: null,
        };
    },
    methods: {
        selectAnswer(answer) {
            if (answer != this.expectedAnswer) {
                alert("Wrong answer!");
            }else {
                alert("Correct answer!");
            }
            this.startQuiz();
        },
        startQuiz () {
            this.isQuizStarted = true;
            this.operandLeft = parseInt(Math.random() * 100000 + 1 );
            this.operandRight = parseInt(Math.random() * 100000 + 1) ;

            const methods = {
                "+": (a,b) => a + b,
                "-": (a,b) => a - b,
                "/": (a,b) => a / b,
                "X": (a,b) => a * b,
            };
            const methodToUse = methods[this.operator];
            this.answers = [];
            let expectedAnswer = null;
            if (this.operator == "/") {
                    this.answers.push((methodToUse(this.operandLeft + 2, this.operandRight + 1)));
                    this.answers.push((methodToUse(this.operandLeft, this.operandRight + 1)));
                    this.answers.push((methodToUse(this.operandLeft + 3, this.operandRight + 2)));
                    expectedAnswer = (methodToUse(this.operandLeft, this.operandRight));
            }else {
                this.answers.push((methodToUse(this.operandLeft + 2, this.operandRight + 1)).toFixed(2));
                this.answers.push((methodToUse(this.operandLeft, this.operandRight + 1)).toFixed(2));
                this.answers.push((methodToUse(this.operandLeft + 3, this.operandRight + 2)).toFixed(2));
                expectedAnswer = (methodToUse(this.operandLeft, this.operandRight)).toFixed(2);
                this.answers[parseInt(Math.random()*this.answers.length)] = expectedAnswer;
            }
            this.expectedAnswer = expectedAnswer; 
        }
    }
}
</script>
<style>
    
</style>