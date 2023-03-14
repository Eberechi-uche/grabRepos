<template>
  <div class="card-container">
    <div class="card-image-container">
      <img src="../../src/assets/git.jpeg" alt="github placeholder image" />
    </div>
    <div class="card-text-container">
      <h3>{{ header }}</h3>
      <p>{{ desc }}</p>
      <div class="flex-wrapper">
        <div class="flex">
          <router-link :to="{ name: 'RepoDetails', params: { id: id } }">
            <button class="card-btn">more</button>
          </router-link>

          <button class="card-btn">{{ liveLink }}</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "desc", "liveLink", "more"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
  background-color: gainsboro;
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
</style>
