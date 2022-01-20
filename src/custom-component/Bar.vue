<template>
  <div ref="dom" class="charts chart-bar"></div>
</template>

<script>
// import echarts from "echarts";

import * as echarts from "echarts";
// console.log('echarts111')
// console.log(echarts)
// import tdTheme from './theme.json'
// import { mapGetters } from 'vuex'
// import { on, off } from '@/libs/tools'
// echarts.registerTheme('tdTheme', tdTheme)
export default {
  name: "ChartBar",
  props: {
    propValue: {
      type: Array,
      default: () => [],
    },
    element: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      dom: null,
    };
  },
  computed: {
    // ...mapGetters(['getAccessId'])
  },
  methods: {
    changeDate() {
      var myChart = echarts.init(this.$refs.dom);
      // 绘制图表
      myChart.setOption({
        title: {
          text: "ECharts 入门示例",
        },
        tooltip: {},
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [5, 20, 36, 10, 10, 20],
          },
        ],
      });

    },
    resize() {
      this.dom.resize();
    },
  },
  mounted() {
    this.$nextTick(() => {
      console.log("echarts111");
      console.log(this.$echarts);
      this.changeDate();
    });
  },
  beforeDestroy() {
    // off(window, "resize", this.resize);
  },
};
</script>
