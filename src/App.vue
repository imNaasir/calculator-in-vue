<template>
  <div class="container">
    <div class="print">{{ data || 0 }}</div>
    <button class="othersigns" @click="clear">C</button>
    <button class="othersigns" >+/-</button>
    <button class="othersigns" @click="percentage">%</button>
    <button class="operators" @click="divide">/</button>
    <button class="numbers" @click="numbers('7')">7</button>
    <button class="numbers" @click="numbers('8')">8</button>
    <button class="numbers" @click="numbers('9')">9</button>
    <button class="operators" @click="mul">x</button>
    <button class="numbers" @click="numbers('4')">4</button>
    <button class="numbers" @click="numbers('5')">5</button>
    <button class="numbers" @click="numbers('6')">6</button>
    <button class="operators" @click="sub">-</button>
    <button class="numbers" @click="numbers('1')">1</button>
    <button class="numbers" @click="numbers('2')">2</button>
    <button class="numbers" @click="numbers('3')">3</button>
    <button class="operators" @click="add">+</button>
    <button class="numbers zero" @click="numbers('0')">0</button>
    <button class="numbers" @click="dot('.')">.</button>
    <button class="operators equal" @click="equal">=</button>
  </div>

  <div>
    <!-- <img src="./" alt=""> -->
  </div>
</template>

<script>
  export default {
    data() {
      return {
        data: '',
        operator: null,
        previos: null,
        isOperatorClicked: false,
      }
    },
    methods: {
      clear() {
        this.data = '';
      },
      percentage(){
        this.data = this.data/100;
      },
      numbers(val) {
        if(this.isOperatorClicked){
          this.data = '';
          this.isOperatorClicked = false;
        }
      this.data = `${this.data}${val}`;
    },
    dot(val) {
      if(this.data.indexOf('.') === -1) {
        if(this.data === '') {
          this.data = '0';
        }
        this.data = `${this.data}${val}`;
        // alert(this.data)
      }
      // alert("val")
    },
    serPrevios(){
      this.previos = this.data
      this.isOperatorClicked = true
    }, 
    divide(){
      this.operator = (a, b) => a / b;
      // alert(a);
      // console.log(a.terget);
      this.serPrevios();
      this.data = ''
      alert(b)
    },
    equal(){
      this.data = `${this.operator(
        parseFloat(this.data),
        parseFloat(this.previos)
      )}`;
      // this.previos = '0';
      alert("success");
    },

    },
 
  }
</script>

<style scoped>
  .container{
    width: 300px;
    margin: 200px auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    grid-gap: 1px;
    background-color: #333;
    padding: 1px;
    border-radius: 10px;
    overflow: hidden;
  }
  .print{
    grid-column: 1/span 4;
    /* background-color: white; */
    padding-right: 10px;
    font-size: 55px;
    color: white;
    text-align: right;
    overflow: auto;
  }
  .numbers{
    background-color: #f2f2f2;
    /* border: 1px solid #999999; */
    font-size: 23px;
 
  }
  .zero{
    grid-column: 1/span 2;
    border-bottom-left-radius: 10px; 
    font-size: 23px;
 
  }
  .equal{
    border-bottom-right-radius: 10px; 
    font-size: 23px;
  }
  .othersigns{
    background-color: #888888;
    /* border: 1px solid #999999; */
    font-size: 23px;
  }
  .operators{
    background-color: orange;
    color: white;
    font-size: 23px;
  }
</style>