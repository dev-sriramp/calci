<template>
<div>
      <span v-for="todo in vari" :key="todo">
        <span v-if="todo === '7' || todo === '4' || todo === '1' || todo === '00'">
          <br/>
          <button @click="mes(todo)" class="button icon twitter">{{ todo }}</button>
        </span>
        <span v-else >
          <button @click="mes(todo)" class="button icon twitter">{{ todo }}</button>
        </span>
      </span>
      <br />
      <h1 v-if="cou !== 0" >{{cou}}</h1>

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
   vari : ['C','X','%','/','7','8','9','*','4','5','6','-','1','2','3','+','00','0','.','='],
    }
  },
  methods: {
    reverseMessage() {
      this.message = this.message
        .split('')
        .reverse()
        .join('')
    },
    mes(e){
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


  .icon {
    position: relative;
    background-color: #ffffff;
    border-radius: 50%;
    padding: 5px;
    margin: 5px;
    width: 50px;
    height: 50px;
    font-size: 18px;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    box-shadow: 0 10px 10px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    transition: all 0.2s cubic-bezier(0.68, -0.55, 0.265, 1.55);
  }

  .icon:hover {
    opacity: 1;
    visibility: visible;
    pointer-events: auto;
  }

  .twitter:hover{
    background-color: #46c1f6;
    color: #ffffff;
  }

.btn {
  color: #42b983;
}

</style>
