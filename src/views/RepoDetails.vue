<script>
import { repositories } from "@/components/Store";
export default {
  props: ["id"],
  data() {
    return {
      repo: {},
    };
  },
  mounted() {
    this.repo = repositories.repos.find((item) => {
      let convertProps = parseFloat(this.$props.id);

      return item.id === convertProps;
    });
    console.log(this.repo.homepage);
  },
};
</script>

<template>
  <h1>{{ repo.name }}</h1>
  <div class="flex">
    <a :href="repo.homepage" target="_blank">
      <p>homepage</p>
    </a>
    <a :href="repo.html_url" target="_blank">
      <p>github</p>
    </a>
  </div>

  <div class="horizontal"></div>
  <p>{{ repo.description }}</p>

  <p>{{ id }}</p>
</template>

<style>
h1 {
  font-size: 10vw;
  font-weight: 900;
  font-family: "Abril Fatface", cursive;
  color: black;
  text-align: start;
}
</style>
