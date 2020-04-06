<template>
  <div>
    <Pixel colorPickerPixel color="white" :current="isCurrent('white')" />
    <Pixel colorPickerPixel color="lightblue" :current="isCurrent('lightblue')" />
    <Pixel colorPickerPixel color="blue" :current="isCurrent('blue')" />
    <Pixel colorPickerPixel color="darkblue" :current="isCurrent('darkblue')" />
  </div>
</template>

<script>
import Pixel from "./Pixel";

export default {
  name: "color-picker",
  components: {
    Pixel
  },
  props: {
    color: String
  },
  methods: {
    isCurrent(color) {
      return this.color === color ? true : false;
    }
  }
};
</script>
