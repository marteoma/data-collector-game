<template>
  <div class="home">
    <input v-model="name" placeholder="Your name"/>
    <h2>Partida {{ $route.params.matchId }}</h2>
    <input v-model="word" />
    <button @click="guess">GUESS!</button>
    <div class="cards">
      <UserCard :guess="guessed" :name="user" v-for="(guessed, user) in users" v-bind:key="user"/>
    </div>
  </div>
</template>

<script>
import UserCard from "@/components/UserCard.vue";
import { ref, set, push, child, onValue, get } from "firebase/database";
import db from '@/db'

export default {
  name: 'MatchView',
  components: {
    UserCard
  },
  data() {
    return {
      word: '',
      user: '',
      users: [],
      name: 'pelirroja',
      guesses: []
    }
  },
  mounted() {
    // this.user = push(listUsers)
    // this.guesses = listUsers
    onValue(ref(db, `matches/${this.$route.params.matchId}/users`), snapshot => {
      this.users = snapshot.val()
    })
  },
  methods: {
    guess: function () {
      set(ref(db, `matches/${this.$route.params.matchId}/users/${this.name}`), this.word)
    }
  },
}
</script>

<style>
.cards {
  display: flex;
  flex-direction: row;
}
</style>