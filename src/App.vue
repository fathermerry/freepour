<template>
  <div class="app" id="app">
    <div class="pattern pattern-on-top"></div>
    <div class="pattern pattern-at-bottom"></div>
    <index v-if="state === 'index'" @changeState="changeState" />
    <div v-else>
      <nav :state="state" />
      <practice v-if="state === 'practice'" @changeState="changeState" />
      <performance v-if="state === 'performance'" @changeState="changeState" />
    </div>
  </div>
</template>

<script>
import Index from './components/Index';
import Practice from './components/Practice';
import Performance from './components/Performance';

export default {
  name: 'App',
  components: {
    Index,
    Practice,
    Performance,
  },
  data() {
    return {
      state: 'index',
    };
  },
  methods: {
    changeState(state) {
      this.state = state;
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
  width: 100%;
  height: 80px;

  &-on-top {
    top: 0;
  }

  &-at-bottom {
    bottom: 0;
  }
}
</style>

