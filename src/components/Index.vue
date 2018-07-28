<template>
  <div class="frame">
    <div class="title">
      <h1>FREE POUR</h1>
      <h3>PRACTICE APP</h3>
    </div>
    <div class="pattern"></div>
    <div class="actions">
      <a href="#" @click.prevent="next('practice')">
        {{ this.log ? 'Continue' : 'Start' }} Practice
      </a>
      <!-- <a href="#" @click.prevent="next('performance')">View Perfomance</a> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data() {
    const [today] = new Date().toLocaleString('en-US').split(', ');
    const log = localStorage.getItem(today);
    return {
      log,
    };
  },
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
  position: absolute;
  left: 0;
  right: 0;
  margin: 0 auto;
  top: 100px;
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
  position: absolute;
  left: 0;
  right: 0;
  margin: 0 auto;
  bottom: 100px;

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
