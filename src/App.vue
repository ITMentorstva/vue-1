
<template>
  <h1>Hello world {{ name }}</h1>

  <p v-if="professor">User is a professor</p>
  <p v-else>User is not a professor</p>

  <p v-if="age >= 18">User is 18+</p>
  <p v-else>User is not 18</p>

  <ol>
    <li v-for="singleClass in classes" :key="singleClass">{{ singleClass }}</li>
  </ol>

  <form @submit.prevent>
    <input v-model="name" type="text" placeholder="Unesite vase ime">
  </form>

  <button v-on:click="changeUserType">Promeni tipa korisnika</button>
</template>

<script>

  export default {
    name: "App",
    data() {
      return {
        name: "Toma",
        professor: false,
        age: 11,
        classes: ['Javascript', 'VueJS', 'ReactJS', 'NodeJS']
      }
    },
    methods: {
      changeUserType() {
        this.professor = !this.professor;
      }
    }
  }
</script>