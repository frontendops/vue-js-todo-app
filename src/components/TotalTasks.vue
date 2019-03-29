<template>
  <div class="task-container" :key="total">
    <div class="title">Total tasks finished</div>
    <svg viewBox="0 0 36 36" class="circular-chart">
      <path
        class="circle-bg"
        d="M18 2.0845
          a 15.9155 15.9155 0 0 1 0 31.831
          a 15.9155 15.9155 0 0 1 0 -31.831"
      ></path>
      <path
        class="low"
        v-bind:class="{ low: low, med: med, high: high}"
        v-bind:stroke-dasharray="stroke"
        d="M18 2.0845
      a 15.9155 15.9155 0 0 1 0 31.831
      a 15.9155 15.9155 0 0 1 0 -31.831"
      ></path>
      <text x="18" y="20.35" class="percentage">{{finished}}/{{total}}</text>
    </svg>
  </div>
</template>

<script>
export default {
  name: "TotalTasks",
  props: ["total", "finished"],
  data() {
    return {
      stroke: `${(this.finished / this.total).toFixed(2) * 100} 100`,
      low: true,
      med: false,
      high: false
    };
  },
  methods: {},
  watch: {
    finished: function() {
      this.stroke = `${(this.finished / this.total).toFixed(2) * 100} 100`;

      if ((this.finished / this.total).toFixed(2) * 100 <= 33) {
        this.low = true;
        this.med = false;
        this.high = false;
      } else if (
        (this.finished / this.total).toFixed(2) * 100 > 34 &&
        (this.finished / this.total).toFixed(2) * 100 <= 68
      ) {
        this.low = false;
        this.med = true;
        this.high = false;
      } else {
        this.low = false;
        this.med = false;
        this.high = true;
      }
    },
    total: function() {
      this.stroke = `${(this.finished / this.total).toFixed(2) * 100} 100`;

      if ((this.finished / this.total).toFixed(2) * 100 <= 33) {
        this.low = true;
        this.med = false;
        this.high = false;
      } else if (
        (this.finished / this.total).toFixed(2) * 100 > 34 &&
        (this.finished / this.total).toFixed(2) * 100 <= 68
      ) {
        this.low = false;
        this.med = true;
        this.high = false;
      } else {
        this.low = false;
        this.med = false;
        this.high = true;
      }
    }
  }
};
</script>

<style scoped>
.title {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 22px;
  font-weight: 800;
  margin-bottom: 15px;
}
.task-container {
  margin-top: 40px;
}
.circular-chart {
  display: block;
  margin: 10px auto;
  max-width: 80%;
  max-height: 250px;
}
.low {
  stroke: #ff9f00;
  fill: none;
  stroke-width: 2.8;
  stroke-linecap: round;
  animation: progress 1s ease-out forwards;
}

.med {
  stroke: #3c9ee5;
  fill: none;
  stroke-width: 2.8;
  stroke-linecap: round;
  animation: progress 1s ease-out forwards;
}

.high {
  stroke: #4cc790;
  fill: none;
  stroke-width: 2.8;
  stroke-linecap: round;
  animation: progress 1s ease-out forwards;
}

.percentage {
  fill: #666;
  font-family: sans-serif;
  font-size: 0.5em;
  text-anchor: middle;
}
.circle-bg {
  fill: none;
  stroke: #eee;
  stroke-width: 3.8;
}
@keyframes progress {
  0% {
    stroke-dasharray: 0 100;
  }
}
</style>