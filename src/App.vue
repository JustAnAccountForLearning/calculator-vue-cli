<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <span style="position: relative;">
      <div class="calc-card"></div>
      <div id="screen-row">
        <CalcScreen :msg="print"/>
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
            <NumberButton number="+"/>
          </div>
          <div>
            <NumberButton number="-"/>
          </div>
          <div>
            <NumberButton number="x"/>
          </div>
          <div>
            <NumberButton number="/"/>
          </div>
           <div>
            <NumberButton number="="/>
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
      yValue: ""
    }
  },
  methods: {
    updateScreen: function(value) {
      // Remove leading zeros
      while (this.print.slice(0,1) == "0") {
        this.print = this.print.slice(1, this.print.length);
      }
      this.print += value;
    },
    
    clearScreen: function() {
      this.print = "";
    },
    
    deleteDigit: function() {
      // Deletes the last digit.
      this.print = this.print.slice(0, this.print.length - 1);
    },
    
    invert: function() {
      if (this.print.slice(0,1) == "-") {
        this.print = this.print.slice(1, this.print.length);
      }
      else {
        this.print = "-" + this.print;
      }
    },

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
  position: relative;
  padding: 20px;
}

#btn-row {
  position: relative;
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
}

#action-btn-col {
  position: relative;
  overflow: hidden;
  float: left;
  width: 51px;
}

.calc-card {
        border: 1px solid rgb(100, 100, 100);
        width: 240px;
        height: 350px;
        position: absolute;
        border-radius: 8px;
        box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }
</style>
