<template>
  <div id="app">
    <img src="https://avatars.mds.yandex.net/i?id=d4d166cbe507d194ba550195dc651b4b-4600186-images-thumbs&ref=rim&n=33&w=300&h=300">
    <div class="display">
      <input  type="number" v-model="operand1" v-on:click="activateOperand(1)"   v-bind:class="{active: activeOperand == 1}"/>
      <input  type="number" v-model="operand2" v-on:click="activateOperand(2)" v-bind:class="{active: activeOperand == 2}"/>
      = <input type="number" v-model="result"/>
      <div v-show="error" class="error">{{ error }}</div>
    </div>

    <div class="action">
      <button v-on:click="sum">+</button>
      <button v-on:click="deduction">-</button>
      <button v-on:click="multiplication">*</button>
      <button v-on:click="division">/</button>
      <button v-on:click="involution">**</button>
    </div>
    <div class="checkbox">
      <input type="checkbox" id="checkbox" v-on:click="keyboard" v-bind:checked="keyboardShow">
      <label for="checkbox">Отобразить экранную клавиатуру</label>
    </div>
    <div v-if="keyboardShow">
      <button v-for="item of itemKeyboard" v-on:click="keyDown(item)" v-bind:key="item">{{item}}</button>
      <button  v-on:click="backspase">-- </button>
    </div>
    <div>
    <input type="radio" name="radio1" id="operand1" value="1" v-on:click="activateOperand(1)">
    <label for="operand1">Операнд 1</label>
    <input type="radio" name="radio1" id="operand2" value="2" v-on:click="activateOperand(2)">
    <label for="operand2">Операнд 2</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      operand1: "",
      operand2: "",
      result: "",
      error: "",
      activeOperand: 1,
      keyboardShow: false,
      itemKeyboard: [0,1,2,3,4,5,6,7,8,9],
    }
  },
  methods: {
    sum() {
      this.result = Number(this.operand1) + Number(this.operand2)
    },
    deduction() {
      this.result = this.operand1 - this.operand2
      this.logList.push(this.result)
    },
    multiplication() {
      this.result = this.operand1 * this.operand2
    },
    division() {
      this.error = "";
      if (this.operand2 == 0) {
        this.error = "На ноль делить нельзя";
      }
      this.result = this.operand1 / this.operand2
    },
    involution() {
      this.result = Math.pow(this.operand1, this.operand2)
    },
    keyboard() {
      this.keyboardShow = !this.keyboardShow

    },
    activateOperand(id) {
      this.activeOperand = id
    },

    keyDown(item) {
      if(this.activeOperand == 1) {
        this.operand1 = this.operand1 == 0 ? '' : this.operand1
        this.operand1 = String(this.operand1) + String(item)
      } else if (this.activeOperand == 2) {
        this.operand2 = this.operand2 == 0 ? '' : this.operand2
        this.operand2 = String(this.operand2) + String(item)
      }
    },
    backspase() {
      if(this.activeOperand == 1) {
        this.operand1 = this.operand1.slice(0, -1)

      } else if (this.activeOperand == 2) {
        this.operand2 = this.operand2.slice(0, -1)
      }
    }
  }

}
</script>
<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 70px;
  border:1px solid darkblue;
}
img {
  width: 50px;
  margin-bottom: 20px;
}
.error {
  border: 1px solid darkred;
  padding: 10px;
  color: red;
  background: coral;

}
.active {
  border: 1px solid coral;
}
</style>
