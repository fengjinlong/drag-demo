<template>
  <!-- <div> -->
  <!-- <p>{{propValue}}</p> -->
  <div ref="dom" class="charts chart-bar"></div>
  <!-- </div> -->
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
      yAxis:0,
    xAxis:0,
    };
  },
  computed: {
    // ...mapGetters(['getAccessId'])
  },
  methods: {
    changeDate() {
      let v = this.xAxis
      let y = this.yAxis
      var myChart = echarts.init(this.$refs.dom);
      // 绘制图表
      myChart.setOption({
        title: {
          text: "ECharts 入门示例",
        },
        tooltip: {},
        xAxis: {
          data: [v, "羊毛衫", "雪纺衫"],
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [y, 20, 36],
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
      this.xAxis = this.element.style.xAxis;
      this.yAxis = this.element.style.yAxis;
      this.changeDate();
    });
  },
  watch: {
    "element.style.xAxis"(v) {
      this.xAxis = v;
      this.changeDate();
    },
    "element.style.yAxis"(v) {
      this.yAxis = v
      this.changeDate();
    }
  },
  beforeDestroy() {
    // off(window, "resize", this.resize);
  },
};
</script>
