<template>
  <h1 style=" margin:10px;font-family:monospace">Calculator</h1>
  <DisplayScreen :output="this.output" />
  <KeyBoard @key-press="updateScreen" />
</template>

<script>
import DisplayScreen from "./components/DisplayScreen.vue";
import KeyBoard from "./components/KeyBoard.vue";

export default {
  name: "App",
  components: {
    DisplayScreen,
    KeyBoard,
  },
  data() {
    return {
      output: "0",
      calval:'0',
      operator: null,
      preCalVal: "",
    };
  },
  methods: {
    updateScreen(output) {
      if (!isNaN(output) || output === ".") {
        if (this.calval === "0") {
          this.output = output;
          this.calval = output;
        } else {
          this.output += output;
          this.calval +=output;
        }
      }
      
      if (output === "C") {
        this.output = "0";
        this.preCalVal='0'
        this.operator=null;
        this.calval='0'
      }
      
      if (output === "%") {
        this.output = this.output / 100;
        this.calval=this.output/100;
      }
      
      if(['+','-','*','/'].includes(output)){
        this.operator = output;
        this.preCalVal=this.calval
        this.output=this.preCalVal+this.operator;
        this.calval=this.preCalVal+this.operator;
      }
      if(output==='='){
        this.output= eval(this.calval);
        this.preCalVal='';
        this.operator=null;
      }
      if (output === "Del") {
        this.output = "0";
        this.preCalVal='0'
        this.operator=null;
        this.calval='0'
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 60px;
}
</style>
