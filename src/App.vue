<template>
  <div class="grid-cntr">
    <button
      class="btn"
      @touchstart="nameCurrentEvent('touchstart')"
      @touchmove="nameCurrentEvent('touchmove')"
      @touchend="nameCurrentEvent('touchend')"
      >Touch me</button
    >
    <button class="btn" v-touch:tap="onTapItem('onTapItem')">Tap me</button>
    <button class="btn" v-touch:swipe="onSwipeItem">Swipe any direction</button>
    <button class="btn" v-touch:swipe.left="onSwipeLeftItem">Swipe left</button>
    <button class="btn" v-touch:drag="onDragItem">Drag me</button>
    <button class="btn" v-touch:press="onPressItem">Press me</button></div
  >

  <p class="output"
    >Current Touch Event:
    <span class="event">{{ name }}</span>
  </p>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "none",
    };
  },
  methods: {
    nameCurrentEvent(name) {
      this.name = name;
    },
    onTapItem(param) {
      return function () {
        alert("You called the " + param + " touch event.");
      };
    },
    onSwipeItem() {
      return (this.name = "swipped");
    },
    onSwipeLeftItem() {
      return (this.name = "swipped left");
    },
    onDragItem() {
      return (this.name = "dragged");
    },
    onPressItem() {
      return (this.name = "pressed");
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.grid-cntr {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  max-width: 500px;
  margin: auto;
}
.btn {
  border: 2px solid rgb(71, 197, 255);
  background-color: rgb(246, 244, 244);
  border-radius: 5px;
  height: 100px;
  font-size: 1rem;
  margin: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.event {
  border-bottom: 1px solid rgb(71, 197, 255);
  color: rgb(113, 113, 113);
}
</style>
