<template>
  <div id="header" :style="{ 'background-color': headerColor }">
    <h1>
      The Great <br />
      <span id="colorDisplay">{{ pickedColor.toUpperCase() }}</span>
      <br />
      Guessing Game
    </h1>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    pickedColor: String,
    headerColor: String,
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
#header {
  transition: all 0.3s;
  background: steelblue;
  text-transform: uppercase;
  text-align: center;
  margin: 0;
  color: white;
}
#colorDisplay {
  font-size: 200%;
}
</style>
