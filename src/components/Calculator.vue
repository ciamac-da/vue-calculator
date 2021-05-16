<template>
  <div class="calculator">
    <div class="display">{{current || 0}}</div>
    <div class="btn" @click="clear">C</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">&percnt;</div>
    <div class="btn operator" @click="divide">&divide;</div>
    <div class="btn" @click="append('7')">7</div>
    <div class="btn" @click="append('8')">8</div>
    <div class="btn" @click="append('9')">9</div>
    <div class="btn operator" @click="times">&times;</div>
    <div class="btn" @click="append('4')">4</div>
    <div class="btn" @click="append('5')">5</div>
    <div class="btn" @click="append('6')">6</div>
    <div class="btn operator" @click="minus">&minus;</div>
    <div class="btn" @click="append('1')">1</div>
    <div class="btn" @click="append('2')">2</div>
    <div class="btn" @click="append('3')">3</div>
    <div class="btn operator" @click="plus">&plus;</div>
    <div class="btn zero" @click="append('0')">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn operator" @click="equals">&equals;</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: "",
      operator: null,
      previous: null,
      operatorClicked: false
    }
  },
  methods : {
    clear(){
      this.current = ""
    },
    sign(){
      this.current = this.current.charAt(0) === "-" ? this.current.slice(1) : `-${this.current}`
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      if(this.operatorClicked) {
        this.current = ""  
        this.operatorClicked = false
      }
      this.current = `${this.current}${number}`
    },
    dot() {
      this.current.indexOf(".") === -1 ? this.append(".") : null
    },
    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    plus() {
      this.operator = (a, b) => a + b
      this.setPrevious()
    },
    minus() {
      this.operator = (a, b) => a-b
      this.setPrevious()
    },
    times() {
      this.operator = (a, b) => a * b
      this.setPrevious()
    },
    divide() {
      this.operator = (a, b) => a / b
      this.setPrevious()
    },
    equals() {
     this.current = `${this.operator(
       parseFloat(this.previous), 
       parseFloat(this.current)
       )}`
       this.previous = null
       this.operator = null
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  width: 375px;
  margin: 0 auto;
}
.display {
  background: gray;
  color: white;
  grid-column: 1/5;
  padding: 15px;
}
.zero {
  grid-column: 1/3;
}
.btn {
  background: #ccc;
  border: 1px solid #999;
  padding: 15px;
  transition: 1s;
}
.btn:hover {
  background: gray;
  transition: 1s;
}
.operator {
  background: orange;
  color: white;
  transition: 1s;
}
.operator:hover {
  background: green;
  transition: 1s;
}
</style>
