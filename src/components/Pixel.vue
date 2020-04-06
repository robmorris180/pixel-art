<template>
  <div @click="handleClick" :class="['pixel', color, current ? 'current' : '']"></div>
</template>

<script>
export default {
  name: "Pixel",
  props: {
    color: String,
    current: Boolean,
    colorPickerPixel: Boolean,
    canvasPixel: Boolean,
    pixelIndex: Number
  },
  methods: {
    handleClick() {
      if (this.colorPickerPixel) {
        this.$root.$emit("update:color", this.color);
      }
      if (this.canvasPixel) {
        this.$root.$emit("clicked:pixel", this.pixelIndex);
      }
    }
  }
};
</script>

<style scoped>
.pixel {
  box-sizing: border-box;
  width: 30px;
  height: 30px;
  border: 1px solid lightgray;
}

.pixel.current {
  border: 4px solid yellow;
}

.white {
  background-color: white;
}

.lightblue {
  background-color: rgb(0, 188, 212);
}

.blue {
  background-color: rgb(3, 169, 244);
}

.darkblue {
  background-color: rgb(33, 150, 243);
}
</style>
