<template>
  <div class="practice">
    <div class="practice-column" id="left">
      <div class="header">
        <div class="header-title">LEFT <br> HAND</div>
        <div class="header-pool">{{ logs.left.pool }}</div>
      </div>
      <div class="counts">
        <a class="count" @click="record('left', 'overpoured')">
          <div class="count-title">Over Poured</div>
          <div class="count-amount">{{ logs.left.counts.overpoured }}</div>
        </a>
        <a class="count" @click="record('left', 'underpoured')">
          <div class="count-title">Under Poured</div>
          <div class="count-amount">{{ logs.left.counts.underpoured }}</div>
        </a>
        <a class="count" @click="record('left', 'correctpour')">
          <div class="count-title">Correct Pour</div>
          <div class="count-amount">{{ logs.left.counts.correctpour }}</div>
        </a>
      </div>
    </div>
    <div class="practice-column" id="right">
      <div class="header">
        <div class="header-title">RIGHT <br> HAND</div>
        <div class="header-pool">{{ logs.right.pool }}</div>
      </div>
      <div class="counts">
        <a class="count" @click="record('right', 'overpoured')">
          <div class="count-title">Over Poured</div>
          <div class="count-amount">{{ logs.right.counts.overpoured }}</div>
        </a>
        <a class="count" @click="record('right', 'underpoured')">
          <div class="count-title">Under Poured</div>
          <div class="count-amount">{{ logs.right.counts.underpoured }}</div>
        </a>
        <a class="count" @click="record('right', 'correctpour')">
          <div class="count-title">Correct Pour</div>
          <div class="count-amount">{{ logs.right.counts.correctpour }}</div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Practice',
  data() {
    const today = `logs_${Date.now()}`;
    function newLog() {
      return {
        left: {
          pool: 50,
          counts: {
            overpoured: 0,
            underpoured: 0,
            correctpour: 0,
          },
        },
        right: {
          pool: 50,
          counts: {
            overpoured: 0,
            underpoured: 0,
            correctpour: 0,
          },
        },
      };
    }

    const logs = localStorage.getItem(today) ? JSON.parse(localStorage.getItem(today)) : newLog();

    return {
      today,
      logs,
    };
  },
  methods: {
    record(hand, type) {
      if (!this.logs[hand].pool) return;
      this.logs[hand].pool -= 1;
      this.logs[hand].counts[type] += 1;
      localStorage.setItem(this.today, {});
    },
  },
};
</script>

<style lang="scss" scoped>
.practice {
  display: flex;
  &-column {
    flex: 1;
    margin-right: 50px;
    &:last-child {
      margin-right: 0;
    }
  }
}

.header {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  > div {
    flex: 1;
  }
  > div:last-child {
    text-align: right;
  }
  &-title {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 18px;
    letter-spacing: 0.01em;
    color: #F9ECDB;
  }
  &-pool {
    font-weight: 500;
    line-height: normal;
    font-size: 36px;
    text-align: right;
    letter-spacing: 0.01em;
    color: #EEC57D;
  }
}

.count {
  padding: 25px;
  background: #F9ECDB;
  border: solid 2px black;
  display: block;
  &:not(:last-child) {
    border-bottom: none;
  }
  &-title {
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    font-size: 18px;
    letter-spacing: 0.01em;
    color: #000000;
    text-transform: uppercase;
  }
  &-amount {
    font-weight: 500;
    line-height: normal;
    font-size: 36px;
    letter-spacing: 0.01em;
    color: #D2C1A9;
  }
}
</style>
