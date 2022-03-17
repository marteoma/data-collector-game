<template>
  <div class="card">
      <h2 class="red">{{ name }}</h2>
      <h5>{{ guess }}</h5>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  props: {
    name: String,
    guess: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
    margin: 0.3em;
    height: 8em;
    width: 8em;
    border: 1px solid black;
}
.red {
    color: red;
}
</style>
