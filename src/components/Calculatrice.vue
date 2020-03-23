<template>
  <div id="app">
    <input
      v-model="nombre1"
      type="number"
    >
    <select v-model="operator">
      <option v-for="option in options" :key="option.text">
        {{ option.text }}
      </option>
    </select>

    <input
      v-model="nombre2"
      type="number"
    >
    {{result}}
  </div>
</template>

<script>

export default {
  name: 'Calculatrice',
  data : function(){
    return {
      nombre1 : 0,
      nombre2 : 0,
      operator: '+',
      options: [
        { text: '+' },
        { text: '-' },
        { text: '/' },
        { text: '*' }
      ]
      }
    },
    computed: {
      result: function () {
        if(this.operator == '+') {
          return(parseInt(this.nombre1) + parseInt(this.nombre2));
        } else if(this.operator == '-') {
          return(parseInt(this.nombre1) - parseInt(this.nombre2));
        }  else if(this.operator == '/') {
          return(parseInt(this.nombre1) / parseInt(this.nombre2));
        } else {
          return(parseInt(this.nombre1) * parseInt(this.nombre2));
        }
      },
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>