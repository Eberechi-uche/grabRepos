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
  <div class="repo-body">
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
  </div>
</template>

<style>
h1 {
  font-size: 10vw;
  font-weight: 900;
  font-family: "Abril Fatface", cursive;
  color: black;
  text-align: start;
}
.flex p {
  margin-right: 10px;
  padding: 10px 0;
  color: rgb(10, 105, 105);
  font-weight: bold;
}
.repo-body {
  padding: 0 30px;
}
</style>
