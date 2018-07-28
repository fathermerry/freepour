<template>
  <nav>
    <div>
      <a href="#" @click.prevent="$emit('back')">
        <img src="../assets/back.svg" alt="Back">
      </a>
    </div>
    <div class="title">
      <h3>FREE POUR</h3>
      <h5>{{ pageTitle }}</h5>
    </div>
    <div></div>
  </nav>
</template>

<script>
export default {
  name: 'navigation',
  props: {
    page: String,
  },
  computed: {
    pageTitle() {
      return this.page === 'practice' ? "TODAY'S PRACTICE" : 'PERFORMANCE';
    },
  },
};
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  margin-bottom: 50px;
  > div {
    min-width: 25px;
  }

  > div:first-child {
    display: flex;
    align-items: center;
  }

  h3 {
    font-style: normal;
    font-weight: bold;
    line-height: normal;
    font-size: 24px;
    text-align: center;
    letter-spacing: 0.01em;
    color: #F2D08B;
    margin: 0 0 5px;
  }

  h5 {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 18px;
    text-align: center;
    letter-spacing: 0.01em;
    color: #F9ECDB;
    margin: 0;
  }

  .title {
    text-align: center;
    flex: 1;
  }
}
</style>
