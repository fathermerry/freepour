<template>
  <div class="frame">
    <div class="title">
      <h1>Free Pour</h1>
      <h3>Practice App</h3>
    </div>
    <div class="pattern"></div>
    <div class="actions">
      <a href="#" @click.prevent="next('practice')">Start Practice</a>
      <a href="#" @click.prevent="next('performance')">View Perfomance</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data() {},
  methods: {
    next(state) {
      this.$emit('next', state);
    },
  },
};
</script>

<style lang="scss" scoped>
.frame {
  position: absolute;
  left: 10px;
  right: 10px;
  top: 10px;
  bottom: 10px;
  background: #F9ECDB;
  padding: 20px;
  text-align: center;
  text-transform: uppercase;
}

.title {
  position: relative;
  top: 150px;
  h1 {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 36px;
    letter-spacing: 0.01em;
    margin: 0;
  }
  h3 {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 18px;
    letter-spacing: 0.01em;
    margin: 5px;
  }
}

.pattern {
  background-image: url('../assets/japanese-pattern-light.png');
  top: 50%;
  transform: translateY(-50%);
  left: 0;
}

.actions {
  position: relative;
  top: 350px;

  a {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 18px;
    text-align: center;
    letter-spacing: 0.01em;
    color: #98683A;
    display: block;
    margin-bottom: 20px;
  }
}
</style>
