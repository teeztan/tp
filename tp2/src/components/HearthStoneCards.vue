<template>
  <div class="hello">    
    <div>
      <ul v-for="(set, index) in cards" :key="index">
          <b>{{index}}</b>      
          <li v-for="card in set" :key="card.cardId">Card : {{card.name}}; Effect : {{card.text}}</li>        
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HearthStoneCards',
  created() {
    this.getAll();
  },
  computed: {
    cards() {
      return this.$store.getters.getCards;
    },
  },
  methods: {
    getAll() {      
      const config = {
          headers: {
            "x-rapidapi-host": "omgvamp-hearthstone-v1.p.rapidapi.com",
            "x-rapidapi-key": "8f63c7eeddmsh9c1c7a90ad44690p1ae244jsn86d02298a4b9"
          }
      };
      axios.get('https://omgvamp-hearthstone-v1.p.rapidapi.com/cards', config)
      .then((response) => {          
          this.$store.commit('setCards', response.data);
      }).catch(error => {
        console.log(error);
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
