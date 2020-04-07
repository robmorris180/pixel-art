<template>
  <div id="app">
    <color-picker :color="color" />
    <Canvas :pixels="pixels" />
  </div>
</template>

<script>
import Canvas from "./components/Canvas.vue";
import ColorPicker from "./components/ColorPicker";

const defaultColor = "white";

export default {
  name: "App",
  components: {
    Canvas,
    ColorPicker
  },
  data() {
    return {
      color: "white",
      pixels: Array(30 * 30)
        .fill()
        .map(() => defaultColor)
    };
  },
  mounted() {
    if (localStorage.getItem("pixels")) {
      try {
        this.pixels = JSON.parse(localStorage.getItem("pixels"));
      } catch (error) {
        localStorage.removeItem("pixels");
      }
    }

    this.$root.$on("update:color", color => {
      this.color = color;
    });

    this.$root.$on("clicked:pixel", index => {
      this.pixels.splice(index, 1, this.color);
      this.saveDrawing();
    });
  },
  methods: {
    saveDrawing() {
      const parsed = JSON.stringify(this.pixels);
      localStorage.setItem("pixels", parsed);
    }
  }
};
</script>

<style>
#app {
  background-color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
