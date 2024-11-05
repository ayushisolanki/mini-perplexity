<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <button @click="fetchMessage">Get Message</button>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      message: "Waiting for API response...",
    };
  },
  methods: {
    async fetchMessage() {
      try {
        const response = await fetch("http://localhost:3000/api/message");
        const data = await response.json();
        console.log({ data });
        this.message = data.message;
      } catch (error) {
        console.error("Error fetching message:", error);
      }
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
