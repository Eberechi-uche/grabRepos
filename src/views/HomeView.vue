<template>
  <div class="home">
    <div class="horizontal"></div>
    <div class="line"></div>
    <div class="left">
      <h1>Projects</h1>
    </div>

    <div class="body">
      <div v-for="repo in repos" :key="repo.id">
        <div class="card-container">
          <div class="card-image-container">
            <img
              src="../../src/assets/git.jpeg"
              alt="github placeholder image"
            />
          </div>
          <div class="card-text-container">
            <h3>{{ repo.name }}</h3>
            <p>{{ repo.description }}</p>
            <div class="flex-wrapper">
              <router-link
                :to="{ name: 'RepoDetails', params: { id: repo.id } }"
              >
                <div class="flex">
                  <button class="card-btn">more</button>
                </div>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import axios from "axios";

export default {
  name: "HomeView",
  data() {
    return {
      repos: [],
    };
  },
  mounted() {
    axios
      .get("https://api.github.com/users/Eberechi-uche/repos")
      .then((response) => {
        this.repos = response.data;
        console.log(response.data);
      });
  },

  components: {
    Card,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Climate+Crisis&family=Mulish:wght@200&display=swap");

.home {
  position: relative;
}
.body {
  padding: 10px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
.left {
  width: 100vw;
  display: flex;
  justify-content: flex-start;
}
.left h1 {
  font-size: 10vw;
  font-weight: 900;
  font-family: "Climate Crisis", cursive;
  color: black;
}
.card-container {
  border: 2px solid black;
  display: grid;
  width: 100%;
  height: fit-content;
  grid-template-columns: 30% auto;
  overflow: hidden;
}
.card-image-container {
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.card-image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.card-text-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 2px 10px;
  height: 100%;
}
.flex-wrapper {
  display: flex;
  justify-content: flex-end;
  padding-bottom: 10px;
}
.flex {
  width: fit-content;
  display: flex;
  justify-content: space-around;
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

@media only screen and (max-width: 600px) {
  .card-container {
    width: 100%;
  }
}
@media only screen and (max-width: 600px) {
  .body {
    grid-template-columns: 1fr;
  }
}
@media only screen and (min-width: 2000px) {
  .body {
    grid-template-columns: 1fr 1fr;
    place-items: center;
    padding: auto;
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
