<template>
  <h1>here is your custom page</h1>

  <div class="horizontal"></div>
  <p>more info about the custom page</p>
  <p>{{ id }}</p>
</template>

<script>
export default {
  props: ["id"],
};
</script>

<style>
h1 {
  font-size: 10vw;
  font-weight: 900;
  font-family: "Climate Crisis", cursive;
  color: black;
}
</style>
