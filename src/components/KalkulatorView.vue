<template>
  <!-- Background setting -->
  <div class="p-3" 
  style="max-width:400px; 
  margin: 50px auto; background:#234">
  
  <!-- Calculator Result -->
  <div class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-vue-dark">
  {{ CalculatorValue || 0}}
  </div>


  <!-- Calculator Button -->
  <div class="row no-gutters">
    <div class="col-3" v-for="n in CalculatorElements" :key="n">
      <div class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
      :class="{'bg-vue-green': ['C','*','/','-','+','%','=',].includes(n)}"
      @click="action(n)"
      >
        {{n}}
      </div>
    </div>
  </div>


  </div>
</template>

<script>
export default {
  name: 'KalkulatorView',
  props: {
    msg: String
  },
  data() {
    return {
      CalculatorValue: '',
      CalculatorElements: ['C','*','/','-',7,8,9,'+',4,5,6,'%',1,2,3,'=',0,'.',],
      operator: null,
      previousCalculatorValue: '',
    }
  },
  methods: {
    action(n) {

      /* Append Value */
      if(!isNaN(n) || n === '.') {
        this.CalculatorValue += n + '';
      }

      /* Clear Value */
      if(n === 'C'){
        this.CalculatorValue = '';
      }
      
      /* Persentage */
      if(n === '%'){
        this.CalculatorValue = this.CalculatorValue / 100 + '';
      }
      
      if(['/','*','-','+'].includes(n)) {
        this.operator = n;
        this.previousCalculatorValue = this.CalculatorValue;
        this.CalculatorValue = '';
      }

      if(n === '='){
        this.CalculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.CalculatorValue
         );

         this.previousCalculatorValue = '';
         this.operator = null;

      }
    }
  },
}
</script>


<style scoped>
.bg-vue-dark {
  background: #31475e;
}

.hover-class:hover {
  cursor: pointer;
  background : #3D5875;
}

.bg-vue-green {
  background: #3fb984;
}
</style>
