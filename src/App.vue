<template>
  <nav>
    <router-link to="/">
      <div class="dot"></div>
    </router-link>

    <router-link to="/joker/opps">to no where</router-link>
    <p>&#169; 2023</p>
  </nav>
  <div class="nav-history">
    <div class="flex">
      <p class="a" @click="back">&#8592;</p>
      <p class="a" @click="forward">&#8594;</p>
    </div>
  </div>
  <router-view />
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
  background-color: #e9e7e7;
  padding: 20px;
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
}
.nav-history {
  padding-left: 20px;
  display: flex;
  width: 100%;
  justify-content: flex-start;
  font-size: 30px;
}
.flex p:hover {
  cursor: pointer;
  transform: scaleX(1.2);
}
</style>
