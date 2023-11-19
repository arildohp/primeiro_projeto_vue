

<template>
    <div class="calculadora">
     <div class="display">0.5342342346</div>
     <div class="btn">C</div>
     <div class="btn">+/-</div>
     <div class="btn">%</div>
     <div class="btn operador">/</div>
     <div class="btn">7</div>
     <div class="btn">8</div>
     <div class="btn">9</div>
     <div class="btn operador">X</div>
     <div class="btn">4</div>
     <div class="btn">5</div>
     <div class="btn">6</div>
     <div class="btn operador">-</div>
     <div class="btn">1</div>
     <div class="btn">2</div>
     <div class="btn">3</div>
     <div class="btn operador">+</div>
     <div class="btn zero">0</div>
     <div class="btn">.</div>
     <div class="btn">=</div>
   
    </div>
   </template>
   
   <script setup> 
       data() {
         return{
           
         }
       }

   </script>
   
   <style scoped>
   .calculadora {
     width: 400px;
     margin: 0 auto;
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