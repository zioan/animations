<template>
  <button type="button" @click="flag = !flag">Toggle</button>

  <transition name="fade" mode="out-in">
    <h1 v-if="flag" key="main">Hello World</h1>
    <h1 v-else key="secondary">Another Hello</h1>
  </transition>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      flag: false,
    };
  },
};
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 0.5s linear;
}
.fade-leave-to {
  transition: all 0.5s linear;
  opacity: 0;
}
</style>
