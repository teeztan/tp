<template>
<div>
    <input v-model="id" type="number">
    <Component2 :id="id"/>
</div>
</template>

<script>

import Component2 from './Component2.vue'

export default {
  name: 'Component1',
  components: {
    Component2
  },
  data: function(){
    return{
      id: 0
    }
  }
}
</script>