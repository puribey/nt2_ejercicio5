<template>
  <div id="container">
    <div
      v-for="(color, i) in gridColors"
      :key="i"
      class="square"
      @click="$emit('click-color', color, i)"
      :style="{ 'background-color': color }"
    ></div>
  </div>
</template>

<script>
export default {
  name: "ColorGrid",
  props: {
    colors: Array,
  },
  data() {
    return {
      gridColors: this.colors,
    };
  },
  watch: {
    colors() {
      this.gridColors = this.colors;
    },
  },
};
</script>

<style scoped>
#container {
  margin: 20px auto;
  max-width: 600px;
}
.square {
  width: 30%;
  background: blue;
  padding-bottom: 30%;
  float: left;
  margin: 1.66%;
  border-radius: 10%;
  transition: background 0.8s;
  -webkit-transition: background 0.8s;
  -moz-transition: background 0.8s;
}
</style>
