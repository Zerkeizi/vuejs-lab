<template>

  <div>
    <h2 class="picture__title" @dblclick="displayImg()">{{ title }}</h2>
    <transition name="picture-fade">
      <div class="picture__frame" v-show="visible">
        <slot/>
      </div>
    </transition>
  </div>

</template>


<script>
import Vue from 'vue';
export default {
  props: ['title'],
  data() {
    return {
      visible: true
    }
  },
  methods: {
    displayImg() {
      this.visible = !this.visible
      // alert(`Vue version : ${Vue.version}`); 2.6.12
    }
  }
}
</script>

<style lang="scss">
   @import './style.scss';
</style>
