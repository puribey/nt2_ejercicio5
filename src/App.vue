<template>
  <div id="app">
    <Header :pickedColor="pickedColor" :headerColor="headerColor" />
    <Navigator
      :isHard="isHard"
      @on-easy="onEasy"
      @on-hard="onHard"
      @restart="restart"
      :messageDisplay="messageDisplay"
      :restartText="restartText"
    />
    <ColorGrid :colors="colors" @click-color="onClickColor" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Navigator from "./components/Navigator.vue";
import ColorGrid from "./components/ColorGrid.vue";

export default {
  name: "App",
  components: {
    Header,
    Navigator,
    ColorGrid,
  },
  mounted() {
    this.restart();
  },
  data() {
    return {
      colorCount: 6,
      isHard: true,
      colors: [],
      pickedColor: "",
      messageDisplay: "",
      restartText: "",
      headerColor: "steelblue",
    };
  },
  methods: {
    restart() {
      this.colors = this.createNewColors(this.colorCount);
      this.pickedColor = this.colors[this.pickColor()];
      this.messageDisplay = "";
      this.restartText = "New Colors!";
    },
    createNewColors(numbers) {
      var arr = [];
      for (var i = 0; i < numbers; i++) {
        arr.push(this.createRandomStringColor());
      }
      return arr;
    },
    createRandomStringColor() {
      var newColor =
        "rgb(" +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ", " +
        this.randomInt() +
        ")";
      return newColor;
    },
    randomInt() {
      return Math.floor(Math.random() * 256);
    },
    pickColor() {
      var quantity;
      if (this.isHard) {
        quantity = 6;
      } else {
        quantity = 3;
      }
      return Math.floor(Math.random() * quantity);
    },
    onEasy() {
      this.isHard = false;
      this.colorCount = 3;
      this.restart();
    },
    onHard() {
      this.isHard = true;
      this.colorCount = 6;
      this.restart();
    },
    onClickColor(color) {
      if (color === this.pickedColor) {
        this.messageDisplay = "You Picked Right!";
        this.colors = this.colors.map(() => this.pickedColor);
        this.restartButton = "Play Again!";
        this.headerColor = this.pickedColor;
      } else {
        this.colors = this.colors.map((c) => (c === color ? "#232323" : c));
        this.messageDisplay = "Try Again!";
      }
    },
  },
  computed: {},
};
</script>

<style>
body {
  background: #232323;
  margin: 0;
  font-family: "Montserrat", "Avenir";
}

h1 {
  font-weight: normal;
  line-height: 1.1;
  padding: 20px 0;
}
</style>
