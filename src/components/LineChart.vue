<template>
  <div class="chart">
    <div class="line1" ref="line1"></div>
  </div>
</template>
<script>
import * as echarts from "echarts";
export default {
  mounted() {
    let line1 = this.$refs.line1;
    let lineChart = echarts.init(line1);
    this.getChart(lineChart);
    window.addEventListener("resize", () => {
      lineChart.resize();
    });
  },
  methods: {
    getChart(lineChart) {
      let option = {
        color: ["#faa", "#55d"],
        // 图表的提示框组件
        tooltip: {
          // 触发方式 item|axis|none
          trigger: "axis",
          textStyle: {
            //
            align: "left",
          },
        },
        // 图例组件
        legend: {
          textStyle: {
            color: "#fff",
          },
          right: "10%",
          // series里面有name则data可以删除
          // data: ['vue','react'],
        },
        // 网格配置
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          show: true, //显示边框
          borderColor: "#faa",
          // 显示刻度标签,包含刻度文字
          containLabel: true,
        },
        // 工具箱组件 可以实现另存为图片等功能
        // toolbox: {
        //   feature: {
        //     saveAsImage: {},
        //   },
        // },
        // x轴相关配置
        xAxis: {
          type: "category",
          // 是否让线条和坐标轴有缝隙
          boundaryGap: false,
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          axisLabel: {
            color: "#fff",
            rotate: "30",
          },
          axisLine: {
            show: true,
            lineStyle: {
              color: "#fff",
            },
          },
          axisTick: {
            show: false,
          },
        },
        yAxis: {
          type: "value",
          axisLabel: {
            color: "#fff",
          },
          axisLine: {
            // show: true,
            lineStyle: {
              color: "#fff",
            },
          },
        },
        // 系列图表配置 决定显示哪种类型的图标
        series: [
          {
            name: "vue",
            type: "line",
            data: [400, 132, 101, 134, 90, 230, 210],
            smooth: true,
            areaStyle: {
              color: {
                type: "linear",
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [
                  {
                    offset: 0,
                    color: "red", // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "blue", // 100% 处的颜色
                  },
                ],
                global: false, // 缺省为 false
              },
            },
          },
          {
            name: "react",
            type: "line",
            data: [200, 182, 191, 234, 290, 330, 310],
            smooth: true,
            // 设置拐点
            symbol: "circle",
            symbolSize: 10,
            showSymbol: false, //鼠标经过才显示拐点
            // 拐点样式
            itemStyle: {
              color: "#0184d5",
              borderColor: "#fff",
              borderWidth: 2,
            },
          },
        ],
      };
      lineChart.setOption(option);
    },
  },
};
</script>
<style scoped lang="less">
.chart {
  .line1 {
    width: 600px;
    height: 300px;
    background: #1d6a96;
  }
}
</style>