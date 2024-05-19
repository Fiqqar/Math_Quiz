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
            isQuizStarted: false
        };
    },
    methods: {
        selectAnswer(answer) {
            if (answer != this.expectedAnswer) {
                alert("Wrong asnwer");
            }
        }
    }
}
</script>
<style>
    
</style>