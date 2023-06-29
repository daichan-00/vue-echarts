<template>
  <div class="chart">
    <div class="bar1" ref="bar1"></div>
    <div class="bar2" ref="bar2"></div>
  </div>
</template>
<script>
import * as echart from "echarts";
export default {
  mounted() {
    // 柱状图1
    let bar1 = this.$refs.bar1;
    let barChart1 = echart.init(bar1);
    this.getChart1(barChart1);
    // 柱状图2
    let bar2 = this.$refs.bar2;
    let barChart2 = echart.init(bar2);
    this.getChart2(barChart2);
    // 图表自适应
    window.addEventListener("resize", () => {
      barChart1.resize();
      barChart2.resize();
    });
  },
  methods: {
    getChart1(barChart) {
      // 配置项设置
      let option = {
        color: ["#73c0de"],
        title: {
          text: "主标题",
          left: "center",
          textStyle: {
            color: "#fff",
          },
          subtext: "副标题",
          subtextStyle: {
            color: "#fff",
          },
        },
        tooltip: {
          trigger: "axis",
          axisPointer: {
            // 指示器类型 line|shadow
            type: "line",
          },
        },
        grid: {
          left: "0%",
          top: "50px",
          right: "0%",
          bottom: "4%",
          containLabel: true,
        },
        xAxis: [
          {
            type: "category",
            data: ["一", "二", "三", "四", "五", "六", "七"],
            // 坐标轴刻度设置
            axisTick: {
              show: false,
              // alignWithLabel: true,
            },
            // x轴的文字颜色和大小
            axisLabel: {
              color: "#fff",
              fontSize: "12px",
            },
            // x轴样式不显示（x轴那条线）
            axisLine: {
              show: false,
            },
          },
        ],
        yAxis: [
          {
            type: "value",
            // y轴文字颜色和大小
            axisLabel: {
              color: "#fff",
              fontSize: "12px",
            },
            // y坐标轴设置
            axisLine: {
              show: true,
              lineStyle: {
                color: "#ccc",
              },
            },
            // y轴分隔线设置
            splitLine: {
              // show: false,
              lineStyle: {
                color: "#ccc",
              },
            },
          },
        ],
        series: [
          {
            name: "name值",
            type: "bar",
            barWidth: "60%",
            data: [10, 52, 200, 334, 390, 330, 220],
            itemStyle: {
              // 修改柱子圆角
              borderRadius: 5,
            },
          },
        ],
      };
      // 实例添加配置项信息
      barChart.setOption(option);
    },
    getChart2(barchart) {
      let color = [
        "#5470c6",
        "#91cc75",
        "#fac858",
        "#ee6666",
        "#73c0de",
        "#3ba272",
      ];
      let option = {
        title: {
          text: "主标题",
          left: "center",
          textStyle: {
            color: "#fff",
          },
        },
        grid: {
          top: "10%",
          left: "4px",
          right: "4px",
          bottom: "5%",
          containLabel: true,
        },
        xAxis: {
          show: false,
        },
        yAxis: [
          {
            type: "category",
            data: ["type1", "type2", "type3", "type4", "type5", "type6"],
            axisLabel: {
              color: "#fff",
            },
            inverse: true,
            axisLine: {
              show: false,
            },
            axisTick: {
              show: false,
            },
          },
          {
            type: "category",
            data: [20, 30, 50, 10, 80, 40],
            axisLabel: {
              color: "#fff",
            },
            inverse: true,
            axisLine: {
              show: false,
            },
            axisTick: {
              show: false,
            },
          },
        ],
        series: [
          {
            name: "填充条",
            type: "bar",
            data: [20, 30, 50, 10, 80, 40],
            // 修改柱子圆角
            itemStyle: {
              borderRadius: 10,
              color: (item) => {
                return color[item.dataIndex];
              },
            },
            // 柱子的宽度
            barWidth: 20,
            // 柱子之间的距离
            barCategoryGap: 10,
            // 柱子内的文字
            label: {
              show: true,
              position: "inside",
              formatter: "{c}%",
            },
            yAxisIndex: 0,
          },
          {
            name: "外框",
            type: "bar",
            data: [100, 100, 100, 100, 100, 100],
            itemStyle: {
              borderRadius: 10,
              color: "none",
              borderWidth: 1,
              borderColor: "#fff",
            },
            yAxisIndex: 1,
            barWidth: 20,
          },
        ],
      };
      barchart.setOption(option);
    },
  },
};
</script>
<style lang="less" scoped>
.chart {
  .bar1,
  .bar2 {
    width: 300px;
    height: 300px;
    background: #1d6a96;
  }
}
</style>