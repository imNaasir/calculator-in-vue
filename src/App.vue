<template>
  <div class="container">
    <div id="print">{{ current || 0 }}</div>
    <button class="othersigns" @click="clear">C</button>
    <button class="othersigns" @click="sign()">+/-</button>
    <button class="othersigns" @click="percentage">%</button>
    <button class="operators" @click="append('/')">/</button>
    <button class="numbers" @click="append('7')" @keypress="keypress">7</button>
    <button class="numbers" @click="append('8')">8</button>
    <button class="numbers" @click="append('9')">9</button>
    <button class="operators" @click="append('*')">x</button>
    <button class="numbers" @click="append('4')">4</button>
    <button class="numbers" @click="append('5')">5</button>
    <button class="numbers" @click="append('6')">6</button>
    <button class="operators" @click="append('-')">-</button>
    <button class="numbers" @click="append('1')">1</button>
    <button class="numbers" @click="append('2')">2</button>
    <button class="numbers" @click="append('3')">3</button>
    <button class="operators" @click="append('+')">+</button>
    <button class="numbers zero" @click="append('0')">0</button>
    <button class="numbers" @click="dot">.</button>
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
      current: '',
      // operator: null,
      // previos: 0,
      // operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign(){
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`
    },
    percentage() {
      this.current = `${parseFloat(this.current)/100}`;
    },
    append(number) {
      this.current = `${this.current}${number}`;
    },
    dot() {
      if (this.current.indexOf('.') === -1) {
        if(this.current === '') {
          this.append('0')
        }
        this.append('.');
      }
    },
    equal() {
      this.current = eval(this.current)
    },
  },
  created() {
    window.addEventListener('keypress', (e) => {
      if (e.key == 0) {
        this.append("0");
      }else if (e.key == 1) {
        this.append("1");
      }else if (e.key == 2) {
        this.append("2");
      }else if (e.key == 3){
        this.append("3")
      }else if (e.key == 4){
        this.append("4")
      }else if (e.key == 5){
        this.append("5")
      }else if (e.key == 6){
        this.append("6")
      }else if (e.key == 7){
        this.append("7")
      }else if (e.key == 8){
        this.append("8")
      }else if (e.key == 9){
        this.append("9")
      }else if (e.key == "/"){
        this.append("/")
      }else if (e.key == "+"){
        this.append("+")
      }else if (e.key == "-"){
        this.append("-")
      }else if (e.key == "*"){
        this.append("*")
      }else if (e.key == "Enter"){
        this.equal()
      }else if (e.key == "%"){
        this.percentage()
      }else if (e.key == "."){
        this.dot()
      }else if (e.key == "c" || e.key == "C") {
        this.clear();
      }else{
        this.current = "";
        this.current = "Not a number";
        document.getElementById("print").style.fontSize = "30px";

      }
    });
  },

}
</script>






<style scoped>
.container {
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

#print {
  grid-column: 1/span 4;
  /* background-color: white; */
  padding-right: 10px;
  font-size: 55px;
  color: white;
  text-align: right;
  overflow: auto;
}

.numbers {
  background-color: #f2f2f2;
  /* border: 1px solid #999999; */
  font-size: 23px;

}

.zero {
  grid-column: 1/span 2;
  border-bottom-left-radius: 10px;
  font-size: 23px;

}

.equal {
  border-bottom-right-radius: 10px;
  font-size: 23px;
}

.othersigns {
  background-color: #888888;
  /* border: 1px solid #999999; */
  font-size: 23px;
}

.operators {
  background-color: orange;
  color: white;
  font-size: 23px;
}
</style>