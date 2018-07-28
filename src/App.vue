<template>
  <div class="app" id="app">
    <div class="pattern pattern-on-top"></div>
    <div class="pattern pattern-at-bottom"></div>
    <transition name="fade">
      <index v-if="page === 'index'" @next="toPage" />
      <div class="content" v-else>
        <navigation :page="page" @back="toPage('index')" />
        <practice v-if="page === 'practice'" />
        <performance v-if="page === 'performance'" />
      </div>
    </transition>
  </div>
</template>

<script>
import Index from './components/Index';
import Navigation from './components/Nav';
import Practice from './components/Practice';
import Performance from './components/Performance';

export default {
  name: 'App',
  components: {
    Index,
    Navigation,
    Practice,
    Performance,
  },
  data() {
    return {
      page: 'index',
    };
  },
  methods: {
    toPage(page) {
      this.page = page;
    },
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Barlow:400,500,700');

* {
  box-sizing: border-box;
}

body, html {
  margin: 0;
  padding: 0;
}

.app {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(180deg, #D17417 0%, #E7A15B 100%);
  font-family: 'Barlow', sans-serif;
}

.pattern {
  position: absolute;
  background: url('./assets/japanese-pattern-dark.png');
  background-repeat: no-repeat;
  background-size: 100% auto;
  width: 100%;
  height: 80px;

  &-on-top {
    top: 0;
  }

  &-at-bottom {
    bottom: 0;
  }
}

.content {
  padding: 35px;
  position: relative;
  z-index: 2;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

