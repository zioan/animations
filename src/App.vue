<template>
  <button type="button" @click="flag = !flag">Toggle</button>

  <transition @enter="enter" @leave="leave" :css="false">
    <h2 v-if="flag">Hello</h2>
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
  methods: {
    enter(el, done) {
      const animation = el.animate([{ transform: "scale3d(0,0,0)" }, {}], {
        duration: 1000,
      });

      animation.onfinish = () => {
        done();
      };
    },

    leave(el, done) {
      const animation = el.animate([{}, { transform: "scale3d(0,0,0)" }], {
        duration: 1000,
      });

      animation.onfinish = () => {
        done();
      };
    },
  },
};
</script>
