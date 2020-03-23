<template>
<div>
    <select v-model="operator">
      <option v-for="option in options" :key="option.text">
        {{ option.text }}
      </option>
    </select>
</div>
</template>
<script>

export default {
  name: 'Mesure',
  props: {
      nb : Number
  },
  data : function(){
    return {
      operator: 'm',
      options: [
        { text: 'm' },
        { text: 'km' },
        { text: 'cm' },
        { text: 'mm' }
      ]
      }
    },
    watch : {
        operator : function () {
            console.log(this.operator);
        }
    },
    computed : {
    result: function () {
        if(this.operator == 'm') {
          return(parseInt(this.nb));
        } else if(this.operator == 'km') {
          return(parseInt(this.nb) / 1000);
        }  else if(this.operator == 'cm') {
          return(parseInt(this.nb) * 100);
        } else {
          return(parseInt(this.nb) * 1000);
        }
      }
  }
}
</script>