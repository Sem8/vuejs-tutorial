
<template>
  <div id="app">
    <!-- displaying something from data -->
    <!-- <h1>
    {{ greeting}}
    </h1>-->

    <!-- v-mode for data binding -->
    <!-- <input v-model='greeting'> -->

    <!-- v-if -->
    <!-- <div v-if="count === 1">Green</div>
    <div v-else-if="count === 2">Red</div>
    <div v-else>Orange</div>-->

    <!-- v-show will set element to display: none; -->
    <!-- <div v-show='count === 1'> Green </div> -->

    <!-- v-bind: takes an html attribute & parses as Javascript -->

    <!-- v-text directive - does the same thing as using {{ }} -->
    <!-- <p v-text="email"> </p> -->

    <!-- v-html directive - same as v-text but can include html tags in it -->
    <!-- <p v-html="email"></p> -->

    <!-- v-once only states the text once and doesn't change again as you change text -->
    <!-- <p v-once>{{ email }} </p>
    <p> {{ email }} </p>-->

    <!-- Sign Up -->
    <!-- <br /> -->
    <!-- v-bind directive with object syntax -->
    <!-- <input v-model="email" :class="{red: email.length < 2}" /> -->

    <!-- v-bind directive with array syntax -->
    <!-- <input v-model="email" :class="[email.length < 2 ? 'red' : 'green']" />
    <br />
    <button onclick="alert('signed up')" v-bind:disabled="email.length < 2">Submit</button>-->

    <!-- v-on add a function to an html element -->
    <!-- <input v-model="newCat" v-on:keyup.enter="addKitty" />
    <button v-on:click="addKitty">+ ADD</button>-->

    <!-- chaining methods to click events like preventDefault() and stop propagation -->
    <!-- <button v-on:click.prevent.stop="addKitty"> + ADD </button> -->

    <!-- Short for v-on:click is @click='addKitty'  -->
    <!-- <button @click="addKitty"> + ADD </button>
    <input v-model="newCat" @:keyup.enter="addKitty">-->

    <!-- v-for - Loops through an array with for in loop -->
    <!-- <ul>       -->
    <!-- <li v-for="cat in catsII" v-bind:key='catsII.indexOf(cat)'>{{ cat.name }}</li> -->
    <!-- <li v-for="cat in cats" v-bind:key='cats.indexOf(cat)'>{{ cat }}</li> -->
    <!-- </ul> -->

    <!-- Vue filters - pipes capitalize function to the cat.name data -->
    <!-- <ul>
      <li v-for="cat in catsII" v-bind:key="catsII.indexOf(cat)">{{ cat.name | capitalize | kittify }}</li>
    </ul>-->

    <p v-on:click="testing">{{ count }} testing</p>

    <!-- Computed methods -->
    <br />
    <!-- {{ kittifyName }} computed keeps giving error, doesn't work -->
    <input v-model="newCat" v-on:keyup.enter="addKitty" />
    <button v-on:click="addKitty">+ ADD</button>
    <ul>
      <li v-for="cat in catsII" v-bind:key="catsII.indexOf(cat)">{{ cat.name }}</li>
    </ul>

    <!-- Doesn't work -->
    <!-- <cat-list :cats='cats' />   -->
  </div>
</template>

<script>
// import Vue from "vue";

/* Doesn't work
Vue.component("cat-list", {
  props: ['catsII'],
  template: `<ul><li v-for="cat in catsII">{{cat.name}}</li></ul>`
});
});
*/



export default {
  name: "App",
  // component: ["cat-list"], // doesn't work
  
  data() {
    return {
      greeting: "Hello Vue",
      count: 2,
      email: "cats@gmail.com",
      cats: ["kitkat", "fish", "henry", "bosco", "melanthios"],
      catsII: [{ name: "kitkat" }, { name: "fish" }, { name: "henry" }],
      newCat: ""
    };
  },
  methods: {
    addKitty: function() {
      this.catsII.push({ name: this.newCat });
      this.newCat = "";
    },
    testing: function() {
      return this.count++;
    }
  },
  filters: {
    capitalize: function(value) {
      return value.toUpperCase();
    },
    kittify: function(value) {
      return value + "y";
    }
  }
  // computed: {
  //   kittifyName: function() {
  //     if (this.newCat.length > 1) {
  //       return this.newCat + "y";
  //     }
  //   }
  // }   // computed doesn't work keeps giving error
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
.red {
  border: 2px solid red;
}
.green {
  border: 2px solid green;
}
</style>
