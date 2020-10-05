<template>
  <div :class="['pixel', color, current ? 'current' : '']" @click="handleClick"></div>
</template>

<script>
export default {
  name: 'Pixel',
  props: {
    color: String,
    current: Boolean,
    isInColorPicker: Boolean,
    isInCanvas: Boolean,
    index: Number
  },
  methods: {
    handleClick: function() {
      if (this.isInColorPicker) {
        this.$root.$emit('updatecolor', this.color)
      }
      if (this.isInCanvas) {
        this.$root.$emit('clickedpixel', this.index)
      }
    }
  }
}
</script>

<style scoped>
.pixel {
  border: 1px solid lightgray;
  width: 30px;
  height: 30px;
  box-sizing: border-box;
}
.white {
  background-color: white;
}
.lightblue {
  background-color: rgb(212, 0, 0);
}
.blue {
  background-color: rgb(3, 7, 244);
}
.darkblue {
  background-color: rgb(33, 243, 44);
}
.pixel.current {
  border: 4px solid yellow;
}
</style>
