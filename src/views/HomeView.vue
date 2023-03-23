<template>
  <div class="home">
    <div class="horizontal"></div>
    <div class="line"></div>
    <div class="left">
      <h1>Projects</h1>
      <img
        class="image-sm"
        src="https://avatars.githubusercontent.com/u/95278948?v=4"
      />
    </div>

    <div class="body">
      <div class="layout">
        <div v-for="(repo, index) in repositories.repos" :key="repo.id">
          <router-link :to="{ name: 'RepoDetails', params: { id: repo.id } }">
            <div class="card-container">
              <div class="card-top-container">
                <p>{{ index }}</p>
                <p>{{ repo.name }}</p>
                <hr />
              </div>
              <div class="card-text-container">
                <p>{{ repo.description }}</p>
              </div>
            </div>
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { repositories } from "@/components/Store.js";

export default {
  name: "HomeView",
  data() {
    return {
      repositories,
    };
  },
  mounted() {
    axios
      .get("https://api.github.com/users/Eberechi-uche/repos")
      .then((response) => {
        repositories.repos = response.data;
        console.log(response.data);
      });
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Abril+Fatface&display=swap");
a {
  all: unset;
}
a:hover {
  cursor: pointer;
}
.home {
  position: relative;
}
.body {
  padding: 10px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  font-size: small;
}
.left {
  width: 100%;
  height: fit-content;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.left h1 {
  font-size: 5vw;
  font-weight: 900;
  font-family: "Abril Fatface", cursive;
  color: black;
}
.card-container {
  border: 1px solid black;
  display: grid;
  place-items: center;
  width: 300px;
  height: 300px;
  grid-template-rows: 60% auto;
  overflow: hidden;
  margin: 10px;
  padding: 10px;
}

.card-top-container p {
  width: 100%;
  font-size: xx-large;
  font-family: "Abril Fatface", cursive;
}

.card-text-container {
  height: fit-content;
}
.flex-wrapper {
  display: flex;
  justify-content: flex-end;
  padding-bottom: 10px;
}
.flex {
  width: fit-content;
  display: flex;
  justify-content: space-evenly;
}
.card-btn {
  background-color: black;
  color: white;
  border: none;
  padding: 10px 20px;
  margin: 0 5px;
  border-radius: 25px;
  height: fit-content;
  width: max-content;
}
.card-btn:hover {
  cursor: pointer;
  border-bottom: 2px;
}
.image-sm {
  width: 35px;
  height: 35px;
  border-radius: 50px;
  object-fit: fill;
}

@media only screen and (min-width: 600px) {
  .body {
    grid-template-columns: 1fr;
    place-items: center;
  }
  .layout {
    grid-template-columns: 1fr 1fr;
  }
}
@media only screen and (min-width: 1020px) {
  .body {
    grid-template-columns: 1fr;
    place-items: center;
  }
  .layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
}
.line {
  position: absolute;
  height: 70px;
  width: 1px;
  background-color: black;
  right: 18px;
  top: -30px;
}
.horizontal {
  height: 1px;
  background-color: black;
}
</style>
