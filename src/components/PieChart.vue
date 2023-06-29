<template>
  <div class="chart">
    <div class="pie1" ref="pie1"></div>
    <div class="pie2" ref="pie2"></div>
  </div>
</template>
<script>
import * as echarts from "echarts";
export default {
  mounted() {
    let pie1 = this.$refs.pie1;
    let pieChart = echarts.init(pie1);
    this.getChart(pieChart);
    let pie2 = this.$refs.pie2;
    let pieChart2 = echarts.init(pie2);
    this.getChart2(pieChart2);
    window.addEventListener("resize", () => {
      pieChart.resize();
      pieChart2.resize();
    });
  },
  methods: {
    getChart(chart) {
      let option = {
        color: ["#73c0de", "#3ba272", "#fc8452", "#9a60b4", "#ea7ccc"],
        title: {
          text: "年龄分布",
          textStyle: {
            color: "#fff",
          },
          left: "center",
          top: "10px",
        },
        tooltip: {
          trigger: "item",
          textStyle: {
            align: "left",
          },
          formatter: "{a} <br/> {b}:{c} ({d}%)",
        },
        legend: {
          bottom: "10px",
          left: "center",
          itemWidth: 10,
          itemHeight: 10,
          textStyle: {
            color: "#fff",
          },
        },
        series: [
          {
            name: "年龄分布",
            type: "pie",
            radius: ["35%", "55%"],
            avoidLabelOverlap: false,
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: 20,
                fontWeight: "bold",
                formatter: "{c}/100",
              },
            },
            data: [
              { value: 8, name: "10岁以下" },
              { value: 12, name: "10-18岁" },
              { value: 10, name: "19-25岁" },
              { value: 50, name: "26-35" },
              { value: 20, name: "35以上" },
            ],
          },
        ],
      };
      chart.setOption(option);
    },
    getChart2(chart) {
      let option = {
        title: {
          text: "地区分布",
          left: "center",
          top: 10,
          textStyle: {
            color: "#fff",
          },
        },
        legend: {
          top: "bottom",
          itemWidth: 10,
          itemHeight: 10,
          textStyle: {
            color: "#fff",
          },
        },
        toolbox: {
          show: true,
          feature: {
            mark: { show: true },
            dataView: { show: true, readOnly: false },
            restore: { show: true },
            saveAsImage: { show: true },
          },
          // icon样式设置
          iconStyle: {
            color: "#fff",
          },
          emphasis: {
            // 鼠标移入时icon及文本设置
            iconStyle: {
              color: "#000",
              textFill: "#000",
            },
          },
        },
        series: [
          {
            name: "分布",
            type: "pie",
            radius: [10, 80],
            // 并图显示模式 radius|area
            roseType: "radius",
            itemStyle: {
              borderRadius: 4,
            },
            // 链接图形和文字的线条
            labelLine: {
              length: 6,
              length2: 8,
            },
            data: [
              { value: 10, name: "rose 1" },
              { value: 20, name: "rose 2" },
              { value: 50, name: "rose 3" },
              { value: 30, name: "rose 4" },
              { value: 20, name: "rose 5" },
              { value: 26, name: "rose 6" },
              { value: 40, name: "rose 7" },
              { value: 30, name: "rose 8" },
            ],
          },
        ],
      };
      chart.setOption(option);
    },
  },
};
</script>
<style scoped lang="less">
.chart {
  .pie1,
  .pie2 {
    width: 300px;
    height: 300px;
    background: #1d6a96;
  }
}
</style>