<template>
  <div class="ase">
    <div>
      <p class="left">
        <strong>{{list.name}}</strong>
        <strong>{{list.surname}}</strong>
        <button class="del" v-on:click="$emit('del-name', index)">Delet</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "nameDispaly",
  props: ["list", "index"]
};
</script>

<style scoped>
* {
  /* background: red; */
}

.ase {
  /* padding-top: 10px;  */
  /* background: blue; */
}
.del {
  background: red;
  color: white;
  margin-left: 4rem;
}
p {
  background: rgb(142, 211, 145);
  border: 2px solid rgb(134, 70, 81);
  width: 100%;
  text-align: center;
}
strong {
  margin-left: 2rem;
}
</style>