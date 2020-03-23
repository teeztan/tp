<template>
<div>
    <p>Je suis le composant {{ id }} </p>
    <Component3/>
</div>  
</template>
<script>
import Component3 from './Component3.vue'

export default {
  name: 'Component2',
  components: {
    Component3
  },
  props: {
      id: Number
  },
  data : function() {
    return {
      message : "Coucou",
      toggle : false,
      liste1 : [
        { id: 1, text: "salut"},
        { id: 2, text: "cava"},
        { id: 3, text: "bien?"}
      ],
      liste2 : [
          { id: 1, text: "oui"},
          { id: 2, text: "non"},
          { id: 3, text: "lol"}
      ],
      liste3 : [
          { id: 1, text: "janni"},
          { id: 2, text: "joudiché"},
          { id: 3, text: "l"}
      ]
    }
  },
  methods: {

  }

}
</script>