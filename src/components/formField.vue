<template>
  <div class="de">
    <form action v-on:submit="addName">
      <input v-model="Names" type="text" required placeholder="FirstName please" /><br />
      <input v-model="surname" type="text" required placeholder="Surname please" /><br />
      <input class="btn" type="submit" value="Add" />
    </form>

    <div v-bind:key="index" v-for="(list, index) in lists">
      <nameDisplay
        v-bind:list="list"
        v-bind:index="index"
        v-on:del-name="$emit('del-name', index)"
      />
    </div>
  </div>
</template>

<script>
import nameDisplay from "./nameDisplay";
export default {
  name: "inputField",
  components: {
    nameDisplay
  },
  props: ["lists"],
  data() {
    return {
      Names: "",
      surname: ''
    };
  },
   mounted () {
    if(localStorage.name) {
      this.name = localStorage.name
    }
  },
  watch: {
    name(newName) {
      localStorage.name = newName
    }
  },
  methods: {
    addName(e) {
      e.preventDefault();
      const newName = {
        name: this.Names,
        surname: this.surname,
        status: "single"
      };
      this.$emit("add-name", newName);
      this.Names = "";
      this.surname = "";
    }
  }
};
</script>

<style scoped>
* {
  /* background: wheat; */
}
.de {
  /* min-height: 30%; */
}

input {
  width: 30%;
  margin: 1%;
  min-height: 2rem;
  border: none;
  border-bottom: 1px solid rgb(140, 153, 22);
}

.btn {
  /* background: rgb(117, 202, 117); */
  background: rgb(71, 99, 40);
  width: 10%;
  padding: 1%;
  border-radius: 1rem;
}
</style>