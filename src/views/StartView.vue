<template>
  <div class="home">
    <input v-model="match_id" />
    <h1>{{ match_id }}</h1>
    <button @click="go()">GO!</button>
  </div>
</template>

<script>
export default {
  name: 'StartView',
  data() {
    return {
      match_id: '',
    }
  },
  methods: {
    go: function () {
      this.$router.push(`/match/${this.match_id}`)
    }
  }
}
</script>

<style>
input {
  text-align: center;
}
</style>
