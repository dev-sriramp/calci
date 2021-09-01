<template>
<div class="calculator">
  <input :class="siz" v-model="cou" disabled/>
<br />
  <div class="calculator-keys">
      <span v-for="todo in vari" :key="todo">
        <span v-if="todo === '7' || todo === '4' || todo === '1' || todo === '00'">
          <button @click="mes(todo)">{{ todo }}</button>
        </span>
        <span v-else >
          <span v-if="todo !== 'C' && todo !=='X' && todo !== '='">
              <button v-if="todo === '+' || todo === '-' || todo === '*' || todo === '/' || todo === '%'" class="operator" @click="mes(todo)">{{ todo }}</button>
             <button v-if="todo !== '+' && todo !== '-' && todo !== '*' && todo !== '/' &&
                todo !== '%'" @click="mes(todo)">{{ todo }}</button></span>
              <span v-else-if="todo === 'C' || todo ==='X'">
                <button class="all-clear" @click="mes(todo)">{{ todo }}</button>
              </span>

              <span v-else>
                <button class="equal-sign" @click="mes(todo)">{{ todo }}</button>
              </span>
        </span>
      </span>
    </div>



  </div>
</template>

<script>
  import { ref } from 'vue'
export default {
  name: 'HelloWorld',
  // props: {
  //   msg: String
  // },

  data() {
    return {
   cou : ref(0),
   siz : ref('cscreen'),
   vari : ['C','X','%','/','7','8','9','*','4','5','6','-','1','2','3','+','00','0','.','='],
    }
  },
  methods: {
    mes(e){
      if(this.cou.length<=6 || this.cou.length=== undefined){
        this.siz='cscreen';
      }
      else if(this.cou.length>=7 && this.cou.length<13){
        this.siz='cscreeni';
      }
      else {
        this.siz='cscreenii';
      }

       if(e == '+' || e == '-' || e == '*' || e == '/' || e == '%' || e == '=' ){
      try {
    this.cou = eval(this.cou).toString();
  }
  catch (err) {
    console.log(err.message)
  }
}
       if(e === 'C'){
         this.cou = 0;
         this.siz='cscreen';
       }
       else if(e==='='){
         this.cou=this.cou.toString();
       }
       else if(e === 'X' ){
         try{
         this.cou=this.cou.substring(0,this.cou.length-1);}
         catch(err)
         {
           console.log(err.message);
         }
       }
       else if(this.cou === 0 || this.cou == 0 || this.cou === '0'){
         this.cou = e.toString();
       }
       else{
         this.cou = this.cou.toString() + e.toString();
       }
     }
}
}
</script>


<style scoped>

  *:focus,
  *:active {
    outline: none !important;
    -webkit-tap-highlight-color: transparent;
  }
button{
  width:50px;
  height:50px;
}
.cscreen {
  width: 92%;
  font-size: 5rem;
  height: 80px;
  border: none;
  background-color: #252525;
  color: #fff;
  text-align: right;
  padding-right: 20px;
  padding-left: 10px;
}
.cscreeni {
  width: 92%;
  font-size: 3rem;
  height: 80px;
  border: none;
  background-color: #252525;
  color: #fff;
  text-align: right;
  padding-right: 20px;
  padding-left: 10px;
}
.cscreenii {
  width: 92%;
  font-size: 1rem;
  height: 80px;
  border: none;
  background-color: #252525;
  color: #fff;
  text-align: right;
  padding-right: 20px;
  padding-left: 10px;
}
.calculator {
  border: 1px solid #ccc;
  border-radius: 5px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
}
.operator {
  color: #337cac;
}
button {
  height: 60px;
  width:80px;
  background-color: #fff;
  border-radius: 3px;
  border: 1px solid #c4c4c4;
  background-color: transparent;
  font-size: 2rem;
  color: #333;
  background-image: linear-gradient(to bottom,transparent,transparent 50%,rgba(0,0,0,.04));
  box-shadow: inset 0 0 0 1px rgba(255,255,255,.05), inset 0 1px 0 0 rgba(255,255,255,.45), inset 0 -1px 0 0 rgba(255,255,255,.15), 0 1px 0 0 rgba(255,255,255,.15);
  text-shadow: 0 1px rgba(255,255,255,.4);
}

button:hover {
  background-color: #eaeaea;
}
.calculator-keys {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-row-gap: 20px;
  grid-column-gap: 20px;
}
.all-clear {
  background-color: #f0595f;
  border-color: #b0353a;
  color: #fff;
}

.all-clear:hover {
  background-color: #f17377;
}
.equal-sign {
  background-color: #2e86c0;
  border-color: #337cac;
  color: #fff;
}

.equal-sign:hover {
  background-color: #4e9ed4;
}

</style>
