<template>
  <div class="app">
    <h2>echarts用例</h2>
    <BarChart />
    <PieChart />
    <LineChart />
  </div>
</template>
<script>
import BarChart from "./components/BarChart";
import PieChart from "./components/PieChart";
import LineChart from "./components/LineChart";
export default {
  components: {
    BarChart,
    PieChart,
    LineChart,
  },
};
</script>
<style lang="less">
.app {
  background: #283b42;
  box-sizing: border-box;
  text-align: center;
  color: #fff;
  padding: 10px;
  & > .chart {
    display: flex;
    margin-bottom: 4px;
    & > div:not(:last-child) {
      margin-right: 4px;
    }
  }
}
</style>