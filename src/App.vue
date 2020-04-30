<template>
  <div id="app">
    <Heading />
    <FormField v-bind:lists="lists" v-on:del-name="delName" v-on:add-name="AddName" />
  </div>
</template>

<script>
import Heading from "./components/layout/heading";
import FormField from "./components/formField";
export default {
  name: "App",
  components: {
    FormField,
    Heading
  },
  data() {
    return {
      lists: [
        { name: "Bright", status: "Student",
        surname: "Adamu"
         },
        {
          name: "Victor",
          status: "Banker",
          surname: 'Bankole'
        },
        {
          name: "Bello",
          surname: "Admeen"
        },
        {
          name: "Tolu",
          surname: "Joseph"
        }
      ]
    };
  },
  mounted() {
    if (localStorage.name) {
      this.name = localStorage.name;
    }
  },
  watch: {
    name(newName) {
      localStorage.name = newName;
    }
  },
  methods: {
    delName(index) {
      this.lists = this.lists.filter((e, x) => x != index);
    },
    AddName(newName) {
      this.lists = [...this.lists, newName]
    }
  },
  created() {
  }
};
</script>

<style>
* {
  margin: 0%;
}
body {
  background: wheat;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
form input {
  border-bottom: thistle;
  background: rgb(71, 99, 40);
  color: whitesmoke;

}
</style>