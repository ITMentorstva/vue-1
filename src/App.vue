
<template>
  <h1>Hello world {{ name }}</h1>

  <p v-if="professor">User is a professor</p>
  <p v-else>User is not a professor</p>

  <p v-if="age >= 18">User is 18+</p>
  <p v-else>User is not 18</p>

  <ol>
    <li v-on:click="deleteClass(singleClass)" v-for="singleClass in classes" :key="singleClass">{{ singleClass }}</li>
  </ol>

  <form @submit.prevent>
    <input v-model="name" type="text" placeholder="Unesite vase ime" />
  </form>

  <form @submit.prevent>
    <input v-model="className" type="text" placeholder="Unesite ime kursa" />
    <input v-on:click="addClass" type="button" value="Dodajte kurs" />
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
        classes: ['Javascript', 'VueJS', 'ReactJS', 'NodeJS'],
        className: null,
      }
    },
    methods: {
      changeUserType() {
        this.professor = !this.professor;
      },

      deleteClass(name) {
        const index = this.classes.indexOf(name); // 0, 1, 2, 3
        this.classes.splice(index, 1);
      },

      addClass() {

        if(this.className === null || this.className.trim() === "") {
          return alert("Morate uneti ime kursa");
        }

        const courses = this.classes.map(val => val.toLowerCase());
        const courseName = this.className.toLowerCase();

        if(courses.includes(courseName)) {
          return alert("Vec imate ovaj kurs");
        }

        this.classes.push(this.className);
      }
    }
  }
</script>