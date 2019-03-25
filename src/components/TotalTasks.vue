<template>
  <div class="task-container">
    <div class="title">Total tasks finished</div>
    <svg viewBox="0 0 36 36" class="circular-chart">
      <path
        class="circle"
        stroke-dasharray="66 100"
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
  props: ["total"],
  data() {
    return {
      finished: 2
    };
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

.circle {
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

@keyframes progress {
  0% {
    stroke-dasharray: 0 100;
  }
}
</style>