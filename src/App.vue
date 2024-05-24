<template>
<div id="app">
  <h1>Math Quiz</h1>
  <OperatorQuiz @onBack="clearOperator" v-if="operator" :operator="operator"/>
  <OperatorSelector v-if="!operator" @changeOperator="changeOperator"/>
</div>
</template>

<script>
import OperatorQuiz from "./components/OperatorQuiz.vue";
import OperatorSelector from "./components/OperatorSelector.vue";

export default {
  name: 'App',
  data () {
    return {
      operator: null
    };
  },
  components: {
    OperatorSelector,
    OperatorQuiz
  },
  methods: {
    clearOperator () {
      this.operator = null;
    },
    changeOperator (op) {
      this.operator = op;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
        padding: 20px;
        margin-right: 20px;
        margin-top: 10px;
        width: 200px;
        height: 80px;
        background-color: #BFAF7E;
        color: #401C14;
        font-size: 15px;
        cursor: pointer;
        vertical-align: top;
}
</style>
