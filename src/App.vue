<template>
  <div id="app">
    <div id="background"><!-- Main background -->
             
        <div id="result">  {{ EqualWasClicked ? result : screen }}  </div>
             
         <div id="main">
            <div id="first-rows">
              <button class="del-bg" id="delete" @click="ClearScreen">Del</button>
              <button value="%" class="btn-style operator opera-bg fall-back">%</button>
              <button value="+" class="btn-style opera-bg value align operator" @click="SetString('+')">+</button>
            </div>
                 
          <div class="rows">
            <button value="7" class="btn-style num-bg num first-child" @click="SetString('7')">7</button>
            <button value="8" class="btn-style num-bg num" @click="SetString('8')">8</button>
            <button value="9" class="btn-style num-bg num" @click="SetString('9')">9</button>
            <button value="-" class="btn-style opera-bg operator" @click="SetString('-')">-</button>
          </div>
                 
          <div class="rows">
            <button value="4" class="btn-style num-bg num first-child" @click="SetString('4')">4</button>
            <button value="5" class="btn-style num-bg num" @click="SetString('5')">5</button>
            <button value="6" class="btn-style num-bg num" @click="SetString('6')">6</button>
            <button value="*" class="btn-style opera-bg operator" @click="SetString('*')">x</button>
          </div>
                 
          <div class="rows">
            <button value="1" class="btn-style num-bg num first-child" @click="SetString('1')">1</button>
            <button value="2" class="btn-style num-bg num" @click="SetString('2')">2</button>
            <button value="3" class="btn-style num-bg num" @click="SetString('3')">3</button>
            <button value="/" class="btn-style opera-bg operator" @click="SetString('/')">/</button>
          </div>
                 
          <div class="rows">
            <button value="0" class="num-bg zero" id="delete">0</button>
            <button value="." class="btn-style num-bg period fall-back">.</button>
            <button value="=" id="eqn-bg" class="eqn align" @click="Calculate">=</button>
          </div>
                
          </div>
         
         </div>
        
  </div>
</template>

<script>
export default{
  data(){
    return{
      result: '0',
      currentValue: '',
      screen: '0',
      equalClicked: false
    }
  },

  computed: {
    EqualWasClicked(){
      return this.equalClicked
    }
  },

  methods: {
    ClearScreen(){
      this.screen = '0'
      this.currentValue = ''

      this.equalClicked = false

    },

    UpdateScreen(){
      this.screen = this.currentValue
    },

    SetString(value){
      this.currentValue += value
      
      this.UpdateScreen()
    },

    ChangeStateEqualClicked(){
      this.equalClicked = true
    },

    Calculate(){
      if(this.currentValue.includes('+') || this.currentValue.includes('-') || this.currentValue.includes('/') || this.currentValue.includes('*')){
        console.log('Selecionou.')
      }else{
        return alert('Selecione um operador.')
      }

      this.result = eval(this.currentValue)

      this.ChangeStateEqualClicked()
    }
  }
}
</script>

<style>
body {
  background:#777;
}

#background {
    background:rgb(228, 124, 202);
    height:400px;
    margin:250px auto;
    transition: all 2s ease;
    width:300px;
}

button {
    border:0;
    color:#fff;
}

#result {
    background:#3b353a;
    border:0;
    color:#fff;
    display:block;
    font-family: sans-serif;
    font-size:20px;
    height:40px;
    letter-spacing: 4px;
    margin:10px auto;
    margin-left: 25px;
    overflow: hidden;
    outline: none;
    padding-top:20px;
    position: relative;
    text-align: right;
    top:10px;
    width:220px;
}

#result:hover {
  cursor: text;
}

#first-rows {
  margin-bottom: 20px;
  position: relative;
  top:10px;
}

.rows {
  margin-top:10px;
  width:300px;
}

#delete {
  border-radius:4px;
  height:50px;
  margin-left:25px;
  width:110px;
}

/* Aligning the division and dot button properly */
.fall-back {
  margin-left:3px !important;
}

/* Aligning the addition and equals to button properly */
.align {
  margin-left: 6px !important;
}

/* Button styling */
.btn-style {
  border-radius:4px;
  height:50px;
  margin-left:5px;
  width:50px;
}

.eqn {
  border-radius:4px;
  height:50px;
  margin-left:5px;
  width:50px;
}

.first-child {
  margin-left:25px;
}


/* Adding background color to the number values */
 .num-bg {
  background:#000;
  border-bottom:3px solid #333;
  color:#fff;
  cursor:pointer;
  font-size:26px;
  outline:none;
}

 .num-bg:active {
  background:#000;
  box-shadow: inset 5px 5px 5px #555;
  color:#fff;
  cursor:pointer;
  font-size:26px;
  outline:none;
}

/*Adding background color to the operator values */ 
.opera-bg {
  background:#333;
  border-bottom:3px solid #555;
  color:#fff;
  cursor: pointer;
  font-size:26px;
  outline:none;
}

.opera-bg:active {
  background:#333;
  box-shadow: inset 4px 4px 4px #555;
  color:#fff;
  cursor: pointer;
  font-size:26px;
  outline:none;
}

/*Adding a background color to the delete button */
.del-bg {
  background:#24b4de;
  border-bottom:3px solid #399cb9;
  color:#fff;
  cursor: pointer;
  font-size:26px;
  outline:none;
}

.del-bg:active {
  background:#24b4de;
  color:#fff;
  font-size:26px;
  cursor: pointer;
  outline:none;
  box-shadow: inset 4px 4px 4px #399cb9;
}

/*Adding a background color to the equals to button */
#eqn-bg {
  background:#17a928;
  border-bottom:3px solid #1f7a29;
  color:#fff;
  cursor: pointer;
  font-size:26px;
  outline:none;
}

#eqn-bg:active {
  background:#17a928;
  box-shadow: inset 4px 4px 4px #1f7a29;
  color:#fff;
  cursor: pointer;
  font-size:26px;
  outline:none;
}


</style>
