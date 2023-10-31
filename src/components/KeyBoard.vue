<template>
  <div class="key-border py-3 px-3" style="max-width:450px; margin:auto; background: #234;">
    <div class="row no-gutters">
      <div class="col-3"  @click="emit(n)" v-for="n in calculatorkeys" :key="n">
        <div class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
        :class="{'green-bg':['%','C','/','x','*','+','-','=','Del'].includes(n)}" >
          {{n}}
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "KeyBoard",
  props: {},
  data(){
    return{
      calculatorkeys:['C','Del','%','=',7,8,9,'+',4,5,6,'-',1,2,3,'*','00',0,'.', '/'],
    }
  },
  methods:{
      emit(a){
          this.$emit('key-press',a+'');
      }
  }
};
</script>
<style scoped>

.key-border {
  border-bottom-left-radius: 5px;
  border-bottom-right-radius: 5px;
  margin-top: 5px;
}
.row {
  display: flex;
}
.bg-vue-dark {
  background: #496481;
}

.green-bg{
  background: rgb(0, 208, 255);
}
.hover-class:hover{
  background: #0095ff;
  cursor: pointer;
}
</style>