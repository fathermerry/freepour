<template>
  <div class="practice">
    <div class="practice-column" v-for="(hand, index) in hands" :key="index">
      <div class="header">
        <div class="header-title">{{ hand }} <br> HAND</div>
        <div class="header-pool">{{ log[hand].pool }}</div>
      </div>
      <div class="counts">
        <a
          class="count"
          v-for="(pour, index) in pours"
          :key="index"
          :class="{'is-highest': isMost(hand, pour)}"
          @click="record(hand, pour)"
        >
          <div class="count-title">{{ title(pour) }}</div>
          <div class="count-amount">{{ log[hand].counts[pour] }}</div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Practice',
  data() {
    const [today] = new Date().toLocaleString('en-US').split(', ');
    const log = localStorage.getItem(today) ? JSON.parse(localStorage.getItem(today)) : {
      tries: 0,
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

    return {
      hands: ['left', 'right'],
      pours: ['overpoured', 'underpoured', 'correctpour'],
      today,
      log,
    };
  },
  methods: {
    title(pour) {
      switch (pour) {
        case 'overpoured':
          return 'Over Poured';
        case 'underpoured':
          return 'Under Poured';
        case 'correctpour':
          return 'Correct Pour';
        default:
      }
      return '';
    },
    record(hand, type) {
      if (!this.log[hand].pool) return;
      this.log[hand].pool -= 1;
      this.log[hand].counts[type] += 1;
      this.log.tries += 1;
      localStorage.setItem(this.today, JSON.stringify(this.log));
    },
    isMost(hand, type) {
      let highestCount = 0;
      let highestVariable;
      const keys = Object.keys(this.log[hand].counts);
      keys.forEach((key) => {
        if (this.log[hand].counts[key] > highestCount) {
          highestCount = this.log[hand].counts[key];
          highestVariable = key;
        }
      });
      return highestVariable === type;
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
    text-transform: uppercase;
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
    .is-highest & {
      color: black;
    }
  }
}
</style>
