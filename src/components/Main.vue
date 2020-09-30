
<template>
  <table>
    <tr>
      <td colspan="3"><input type="text" v-model="result"></td>
      <td><v-btn value="C" @click="clear">C</v-btn></td>
    </tr>
    <tr v-for="(items, i) in item" :key="i">
      <td v-for="(NumberAndFormula, j) in items" :key="j">
        <v-btn @click="calculation(NumberAndFormula)">{{NumberAndFormula}}</v-btn>
      </td>
    </tr>
  </table>
</template>

<script>
  import Vue from 'vue'
  export default {
    name:'Main',
    data:()=>({
      result:'0',
      item:[
        ['7', '8', '9', '/'],
        ['4', '5', '6', '*'],
        ['1', '2', '3', '-'],
        ['0', '.', '+', '=']
      ]
    }),

    methods:{
      clear:function(){
        this.result = '0'
      },

      calculation:function(type){
        if(type === '='){
          this.result = eval(this.result)
        }

        else if(this.result === '0'){
          this.result = type
        }

        else {
          this.result += type
        }
      }
    }
  }

</script>
