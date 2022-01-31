<template>
  <div class="row q-col-gutter-sm  q-py-sm">
    <div class="col-lg-6 col-md-6 col-sm-12 col-xs-12">
      <q-card class="q-ma-xs" style="background-color: #38b1c5">
        <q-card-section class="text-h6 text-white">
          주별 큐티 내역
        </q-card-section>
        <q-card-section class="q-pa-none">
          <div ref="barchart" id="barchart" style="height: 250px;"></div>
        </q-card-section>
      </q-card>
    </div>
    <q-resize-observer @resize="onResize"/>
  </div>
</template>

<script>
import {defineComponent, defineAsyncComponent} from 'vue';

export default defineComponent({
  name: 'CardCharts',
  setup () {
    return {
      BarChart: {
        "tooltip": {"show": true},
        "title": {"show": true, "textStyle": {"color": "rgba(0, 0, 0 , .87)", "fontFamily": "sans-serif"}},
        "grid": {"containLabel": true, "bottom": "10%", "top": "5%"},
        "xAxis": {
            "axisLabel": {"show": true},
            "type": "category",
            "axisLine": {
                "show": false,
                "lineStyle": {"color": "rgba(255, 255, 255 , 1.0)"}
            },
            "axisTick": {
                "show": false,
                "alignWithLabel": true,
                "lineStyle": {"show": true, "color": "rgba(0, 0, 0 , .54)"}
            },
            
        },
        "yAxis": {
            "show": false,
            "type": "value",
            "axisLine": {"lineStyle": {"color": "rgba(0, 0, 0 , .54)"}},
            "axisLabel": {"show": false},
            "splitLine": {"lineStyle": {"type": "dashed"}},
            "axisTick": {
                "show": false,
                "lineStyle": {"show": true, "color": "rgba(0, 0, 0 , .54)"}
            }
        },
        "series": [{
            "type": "bar",
            "barGap": "-100%",
            "itemStyle": {"normal": {"color": "rgba(0,0,0,0.1)"}},
            "barWidth": "50%"
        }, {"barWidth": "50%", "type": "bar", "itemStyle": {"normal": {"color": "#ffffff"}}}],
        "dataset": {
            "source": [{"label": "21.48", "max": 6, "횟수": 3}, {
                "label": "21.50",
                "max": 6,
                "횟수": 4
            }, {"label": "21.49", "max": 6, "횟수": 3}, {
                "label": "21.51",
                "max": 6,
                "횟수": 4
            }, {"label": "21.52", "max": 6, "횟수": 2}, {
                "label": "22.1",
                "max": 6,
                "횟수": 5
            }, {
                "label": "22.2",
                "max": 6,
                "횟수": 6
            }, {
                "label": "22.3",
                "max": 6,
                "횟수": 5
            }, {"label": "22.4", "max": 6, "횟수": 4}]
        }
    },
      bar_chart: null
    }
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      let theme = this.model ? 'dark' : 'light';
      let barchart = document.getElementById('barchart');
      echarts.dispose(barchart);
      this.bar_chart = echarts.init(barchart, theme);
      this.bar_chart.setOption(this.BarChart)
    },
    onResize() {
      if (this.bar_chart) {
        this.bar_chart.resize();
      }
    }
  }
})
</script>
