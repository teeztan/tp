<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <calculatrice/>
    <mesure nb=3 />
    <carrousel />
    <span v-if="toggle">{{message}}</span>
    <input v-if="toggle" v-model="message" type="text">
    <ol v-if="!toggle">
      <li v-for ="todo in todos" :key="todo">
        {{todo.text | capitalize}}
        </li>
      </ol>

      <ol>
        <li v-for="image in images" :key="image">
          </li>
        </ol>

    <form action="" method="post" @submit="checkForm">
      <p v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors" :key="error">{{ error }}</li>
    </ul>
  </p>
    <div>
        <label for="name">Nom :</label>
        <input type="text" id="name" name="user_name" maxlength="15" v-model="name">
    </div>
    <div>
        <label for="surname">Prenom :</label>
        <input type="text" id="surname" name="user_surname" maxlength="15" v-model="surname">
    </div>
    <div>
        <label for="mail">Mail :</label>
        <input type="email" id="mail" name="user_mail" v-model="email">
    </div>
    <div>
        <label for="phone">Téléphone :</label>
        <input type="number" id="phone" name="user_phone" v-model="phone">
    </div>
    <div>
        <label for="date">Date de naissance :</label>
        <input type="date" id="date" name="user_date">
    </div>
    <div>
        <input type="radio" id="male" name="gender" value="male">
        <label for="male">Male</label><br>
        <input type="radio" id="female" name="gender" value="female">
        <label for="female">Female</label><br>
        <input type="radio" id="other" name="gender" value="other">
        <label for="other">Other</label>
    </div>
    <div id="myDiv" ref="myDiv">
      <input type="submit" value="Envoyer" disabled="disabled">
    </div>
    </form>
    <button @click="toggle=!toggle">afficher</button>
  </div>
</template>

<script>

import calculatrice from './components/Calculatrice.vue'
import mesure from './components/Mesure.vue'
import carrousel from './components/Carrousel.vue'

export default {
  name: 'App',
  components: {
    calculatrice,
    mesure,
    carrousel
  },
  data : function() {
    return {
       errors:[],
      name:null,
      phone:null,
      disabled: "",
      email:null,
      surname:null,
      message : "Coucou",
      toggle : false,
      todos : [
        { text: "salut"},
        { text: "cava"},
        { text: "bien?"}
      ],
      images : [
         '../assets/test.png',
        '../assets/test2.png',
        '../assets/test3.png'
      ]
    }
  },
  filters: {
      capitalize: function(value) {
        return value.toUpperCase()
      }
  },
  methods: {
    checkForm:function(e) {
      this.errors = [];
      if(!this.name) this.errors.push("Name required.");
      if(!this.name) this.errors.push("Surname required.")
      if(!this.email) {
        this.errors.push("Email required.");
      } else if(!this.validEmail(this.email)) {
        this.errors.push("Valid email required.");        
      }
      if(!this.phone) {
        this.errors.push("Phone number required");
      } else if(!this.validPhone(this.phone)) {
        this.errors.push("Valid phone number required")
      }
      if(!this.errors.length) return true;
      e.preventDefault();
    },
    validEmail:function(email) {
      var re = /^(([^<()[\]\\.,;:\s@\]+([^<()[\]\\.,;:\s@\]+)*)|(.+))@(([[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}.[0-9]{1,3}])|(([a-zA-Z-0-9]+.)+[a-zA-Z]{2,}))$/;
    return re.test(email);
    },
     validPhone:function(phone) {
      var re = /^\d{10}$/;
      return re.test(phone)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialias ed;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
