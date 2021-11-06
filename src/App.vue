<template>
  <button type="button" @click="flag = !flag">Toggle</button>

  <!-- <transition name="fade" mode="out-in">
    <h1 v-if="flag" key="main">Hello World</h1>
    <h1 v-else key="secondary">Another Hello</h1>
  </transition> -->
  <!-- <transition name="zoom" appear>
    <h2 v-if="flag">Hello</h2>
  </transition> -->

  <transition
    @before-enter="beforeEnter"
    @enter="enter"
    @after-enter="afterEnter"
    @before-leave="beforeLeave"
    @leave="leave"
    @after-leave="afterLeave"
    :css="false"
  >
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
    beforeEnter(el) {
      console.log("beforeEnter event", el);
    },
    enter(el, done) {
      const animation = el.animate([{ transform: "scale3d(0,0,0)" }, {}], {
        duration: 1000,
      });

      animation.onfinish = () => {
        done();
      };
    },
    afterEnter(el) {
      console.log("afterEnter event", el);
    },
    beforeLeave(el) {
      console.log("beforeLeave event", el);
    },
    leave(el, done) {
      const animation = el.animate([{}, { transform: "scale3d(0,0,0)" }], {
        duration: 1000,
      });

      animation.onfinish = () => {
        done();
      };
    },
    afterLeave(el) {
      console.log("afterLeave event", el);
    },
  },
};
</script>

<style>
h2 {
  widows: 400px;
  padding: 20px;
  margin: 20px;
}
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

/* .zoom-enter-from {
    opacity: 0;
  } */
.zoom-enter-active {
  animation: zoom-in 1s linear forwards;
}
.zoom-leave-to {
  animation: zoom-out 1s linear forwards;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }
  to {
    transform: scale(1, 1);
  }
}
@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }
  to {
    transform: scale(0, 0);
  }
}
</style>
