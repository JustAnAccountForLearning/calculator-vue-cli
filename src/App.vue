<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <span style="position: relative;">
      <div class="calc-card">
        <div id="screen-row">
          <CalcScreen :msg="print" :backgroundActive="screenColor" />
        </div>
        <div id="btn-row">
          <div id="num-btn-col">
            <div id="num-btn-row">
                <NumberButton number="AC" @update="clearScreen()" />
                <NumberButton number="DEL" @update="deleteDigit()" />
                <NumberButton number="+/-" @update="invert()" />
            </div>
            <div id="num-btn-row">
                <NumberButton number="7" @update="updateScreen('7')" />
                <NumberButton number="8" @update="updateScreen('8')" />
                <NumberButton number="9" @update="updateScreen('9')" />
            </div>
            <div id="num-btn-row">
                <NumberButton number="4" @update="updateScreen('4')" />
                <NumberButton number="5" @update="updateScreen('5')" />
                <NumberButton number="6" @update="updateScreen('6')" />
            </div>
            <div id="num-btn-row">
                <NumberButton number="1" @update="updateScreen('1')" />
                <NumberButton number="2" @update="updateScreen('2')" />
                <NumberButton number="3" @update="updateScreen('3')" />
            </div>
            <div id="num-btn-row">
                <NumberButton number="." @update="updateScreen('.')" />
                <NumberButton number="0" @update="updateScreen('0')" />
                <NumberButton number="00" @update="updateScreen('00')" />
            </div>
          </div>
          <div id="action-btn-col">
            <div>
              <NumberButton number="+" @update="storeInitialData('+')" />
            </div>
            <div>
              <NumberButton number="-" @update="storeInitialData('-')" />
            </div>
            <div>
              <NumberButton number="x" @update="storeInitialData('x')" />
            </div>
            <div>
              <NumberButton number="/" @update="storeInitialData('/')" />
            </div>
            <div>
              <NumberButton number="=" @update="calculateResult()" />
            </div>
          </div>
          </div>
      </div>
    </span>
  </div>
</template>

<script defer>
import CalcScreen from './components/CalcScreen.vue'
import NumberButton from './components/NumberButton.vue'

export default {
  name: 'app',
  data() {
    return {
      print: "",
      xValue: "",
      yValue: "",
      symbol: "",
      screenColor: "white"
    }
  },
  methods: {
    updateScreen: function(value) {
      // Clear the screen to start fresh if a value was recently calcuated
      if (this.symbol == "=") {
        this.clearScreen();
        this.symbol = "";
      }

      // Remove leading zeros
      while (this.print.slice(0,1) == "0") {
        this.print = this.print.slice(1, this.print.length);
      }
      
      // Show error when trying to use too many digits
      if (this.print.length > 14) {
        this.flash();
        return;
      }

      this.print += value;
    },
    
    clearScreen: function() {
      this.print = "";
    },
    
    deleteDigit: function() {
      // Deletes the last digit.
      this.print = this.print.slice(0, this.print.length - 1);

      // TODO: 
      // Allow the ability to remove the last inputed symbol and retain the value (use xValue)
    },
    
    invert: function() {
      if (this.print.slice(0,1) == "-") {
        this.print = this.print.slice(1, this.print.length);
      }
      else {
        this.print = "-" + this.print;
      }
    },

    storeInitialData: function(value) {
      if (this.print != "") {
        this.xValue = Number(this.print);
      }
      this.symbol = value;
      this.clearScreen();
    },

    calculateResult: function() {
      this.yValue = Number(this.print);
      if (this.symbol == "+") {
        this.print = String(this.xValue + this.yValue);
      }
      if (this.symbol == "-") {
        this.print = String(this.xValue - this.yValue);
      }
      if (this.symbol == "x") {
        this.print = String(this.xValue * this.yValue);
      }
      if (this.symbol == "/") {
        this.print = String(this.xValue / this.yValue);
      }

      // Set symbol equal to '=' so it will reset in updateScreen
      this.symbol = "=";
    },

    flash: function() {
      this.screenColor = "grey";
      setTimeout(function() {
        this.screenColor = "white";
      }.bind(this), 100);
    }

  },
  components: {
    CalcScreen,
    NumberButton
  }, 
}


</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  position: relative;
}

#screen-row {
  position: absolute;
  padding: 20px;
  margin: 0;
  height: 30px;
  z-index: 1;
}

#btn-row {
  position: absolute;
  top: 75px;
  padding-left: 15px;
  overflow: hidden;
  width: 260px;
}

#num-btn-row {
  position: relative;
  overflow: hidden;
  width: 160px;
}

#num-btn-col {
  float: left;
  height: 260px;
  position: relative;
}

#action-btn-col {
  position: relative;
  overflow: hidden;
  float: left;
  width: 51px;
}

.calc-card {
  text-align: center;
  border: 1px solid rgb(100, 100, 100);
  background-color: #546e86ab;
  z-index: -2;
  width: 240px;
  height: 350px;
  position: absolute;
  left: 50%;
  margin-left: -225px;
  border-radius: 8px;
  box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23), inset 0 0 3px #101229;
}
</style>
