<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/books">Books</router-link> |
      <router-link to="/animals">Animals</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "Hello Vue!",
    };
  },
  methods: {
    // TODO: Add methods
    test() {
      console.log("test");
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
