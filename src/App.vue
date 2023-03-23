<template>
  <nav>
    <router-link to="/">
      <div class="dot-container">
        <div class="dot"></div>
      </div>
    </router-link>

    <router-link to="/joker/opps">to no where</router-link>
    <a href="https://github.com/Eberechi-uche" target="_blank">
      <img
        class="image-sm"
        src="https://avatars.githubusercontent.com/u/95278948?v=4"
      />
    </a>
  </nav>
  <div class="nav-history">
    <div class="flex">
      <p class="a" @click="back">&#8592;</p>
      <p class="a" @click="forward">&#8594;</p>
    </div>
  </div>
  <div class="router-children">
    <router-view />
  </div>
</template>
<script>
export default {
  methods: {
    back() {
      this.$router.go(-1);
    },
    forward() {
      this.$router.go(1);
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Mulish:wght@200&display=swap");

#app {
  font-family: "Mulish", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 20px;
  width: 100%;
  height: max-content;
}
a {
  text-decoration: none;
}

nav {
  padding: 30px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

nav a.router-link-exact-active {
}
.dot {
  width: 10px;
  height: 10px;
  background-color: black;
  margin: 3px;
  background-color: rgb(10, 105, 105);
}
.nav-history {
  padding-left: 20px;
  display: flex;
  width: 100%;
  justify-content: flex-start;
  font-size: 30px;
}
.flex p {
  margin: 0 5px 0;
}
.flex p:hover {
  cursor: pointer;
  transform: scaleX(1.2);
  transition: transform 0.4s ease-in-out;
}
.dot-container {
  border: 2px solid rgb(10, 105, 105);
}
</style>
