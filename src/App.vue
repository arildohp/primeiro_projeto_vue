

<template>
 <div class="calculadora">
  <div class="display">{{current || '0'}}</div>
  <div @click="clear" class="btn">C</div>
  <div @click="sign" class="btn">+/-</div>
  <div @click="percentual" class="btn">%</div>
  <div @click="divisao" class="btn operador">/</div>
  <div @click="append('7')" class="btn">7</div>
  <div @click="append('8')"  class="btn">8</div>
  <div @click="append('9')"  class="btn">9</div>
  <div @click="multiplicacao" class="btn operador">X</div>
  <div @click="append('4')"  class="btn">4</div>
  <div @click="append('5')"  class="btn">5</div>
  <div @click="append('6')"  class="btn">6</div>
  <div @click="subtracao" class="btn operador">-</div>
  <div @click="append('1')"  class="btn">1</div>
  <div @click="append('2')"  class="btn">2</div>
  <div @click="append('3')"  class="btn">3</div>
  <div @click="somar" class="btn operador">+</div>
  <div @click="append('0')" class="btn  zero ">0</div>
  <div @click="dot" class="btn">.</div>
  <div @click="igual" class="btn operador">=</div>

 </div>
</template>
<script >
    export default {
      data () {
        return {
          previous: null,
          current: '',
          operator: null,
          operatorClicked: false,
        }
      },
      methods: {
        clear() {
          this.current = '';
        },

        sign() {
          this.current = this.current.charAt(0) === '-' ?
           this.current.slice(1) : `-${this.current}`;
        },
                
        append(number) {
          if (this.operatorClicked) {
            this.current = ''
            this.operatorClicked = false;
          }
          this.current = `${this.current}${number}`;
        },

        dot() {
          if (this.current.indexOf('.') === -1){
            this.append('.');
          }
        },

        setPrevious() {
         this.previous = this.current;
         this.operatorClicked = true;
        },

        percentual() {
          this.current = `${parseFloat(this.current) / 100}`;
        },

       divisao () {
         this.operator = (a, b) => a / b;    
         this.setPrevious();     
       },

       multiplicacao() {
         this.operator = (a, b) => a * b; 
         this.setPrevious();       
       },

       subtracao() {
         this.operator = (a, b) => a - b; 
         this.setPrevious();         
       },

       somar() {
         this.operator = (a, b) => a + b;    
         this.setPrevious();     
       },

       igual() {
       if (this.operator && this.previous) {
        const result = this.operator(parseFloat(this.previous),parseFloat(this.current));
        this.current = result.toString();
        this.previous = null;
        this.operatorClicked = true;
         }
       }
    }   
  }
</script>


<style scoped>
.calculadora {
  width: 400px;
  margin: 100px auto;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  }  
.display {
    grid-column: 1/5;
    background-color: #333;
    color: white;
  }
  .zero{
    grid-column: 1/3;
  }
  .btn{
    background-color: #eee;
    border: 1px solid #999;
    font-size: 40px;
  }
  .operador{
    background-color: orange;
    color: white;
  }
</style>



