<template>
  <div class="canvas">
    <Pixel
      canvasPixel
      v-for="(color, index) in pixels"
      :key="index"
      :color="color"
      :pixelIndex="index"
    />
  </div>
</template>

<script>
import Pixel from "./Pixel";

export default {
  name: "Canvas",
  components: {
    Pixel
  },
  props: {
    pixels: Array
  }
};
</script>

<style scoped>
.canvas {
  display: flex;
  flex-wrap: wrap;
  max-width: calc(30 * 30px); /** 900px */
}
</style>
