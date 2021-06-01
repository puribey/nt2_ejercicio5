<template>
  <div id="navigator">
    <button id="reset" @click="$emit('restart')">{{ restartText }}</button>
    <span id="message">{{ messageDisplay }} </span>

    <button id="easy" :class="!isHard && 'selected'" @click="$emit('on-easy')">
      easy
    </button>
    <button id="hard" :class="isHard && 'selected'" @click="$emit('on-hard')">
      hard
    </button>
  </div>
</template>

<script>
export default {
  name: "Navigator",
  props: {
    isHard: Boolean,
    messageDisplay: String,
    restartText: String,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
#navigator {
  background: #ffffff;
  height: 30px;
  text-align: center;
  margin: 0;
  margin-top: -30px;
}
#message {
  color: #ffffff;
  display: inline-block;
  width: 20%;
}
.selected {
  background-color: steelblue;
  color: white;
}
button {
  border: none;
  background-color: white;
  font-family: "Montserrat", "Avenir";
  text-transform: uppercase;
  height: 100%;
  font-weight: 700;
  letter-spacing: 1px;
  color: steelblue;
  transition: all 0.3s;
  outline: none;
}
button:hover {
  color: white;
  background-color: steelblue;
}
</style>
