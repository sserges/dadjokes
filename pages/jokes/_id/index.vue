<template>
  <div>
    <nuxt-link to="/jokes">
      Back To Jokes
    </nuxt-link>
    <h2>{{ joke }}</h2>
    <hr>
    <small>
      {{ $route.params.id }}
    </small>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      joke: {}
    }
  },
  async created () {
    const config = {
      headers: {
        Accept: 'application/json'
      }
    }

    try {
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config)
      this.joke = res.data.joke
    } catch (error) {
      // eslint-disable-next-line no-console
      console.error(error)
    }
  }
}
</script>

<style></style>
