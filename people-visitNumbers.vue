<template>
  <div class="top_box">
      <div class="tourNumbers">
        <div class="chart" ref="chart"></div>
      </div>
      <div class="dayNumbers">
        <img src="../../../assets/img/people/tourist_numbers.png" alt="">
        <div>
          <div class="tips">当天累计游客量</div>
          <div class="numbers"><span><run-num :num="5272"></run-num></span>人</div>
        </div>
      </div>
    </div>
</template>

<script>
import RunNum from '@/components/run-num'
import echarts from 'echarts'
require('echarts-wordcloud')
export default {
  components: {
    'run-num': RunNum
  },
  data () {
    return {}
  },
  mounted () {
    this.initChart()
  },
  methods: {
    initChart () {
      this.chart = echarts.init(this.$refs.chart)
      var data = [{
        'name': '0',
        'value': 701
      }, {
        'name': '1',
        'value': 800
      }, {
        'name': '2',
        'value': 626
      }, {
        'name': '3',
        'value': 480
      }, {
        'name': '4',
        'value': 220
      }, {
        'name': '5',
        'value': 220
      }, {
        'name': '6',
        'value': 220
      }, {
        'name': '7',
        'value': 220 }, { 'name': '8', 'value': 220 }, { 'name': '9', 'value': 220 }, { 'name': '10', 'value': 220 }, { 'name': '11', 'value': 220 }, { 'name': '12', 'value': 220 }, { 'name': '13', 'value': 220 }, { 'name': '14', 'value': 220 }, { 'name': '15', 'value': 220 }, { 'name': '16', 'value': 220 }, { 'name': '17', 'value': 220 }, { 'name': '18', 'value': 220 }, { 'name': '19', 'value': 220 }, { 'name': '20', 'value': 220 }, { 'name': '21', 'value': 220 }, { 'name': '22', 'value': 220 }, { 'name': '23', 'value': 220 }, { 'name': '24', 'value': 220 }]
      var xData = []
      var yData = []
      var min = 0
      data.map(function (a, b) {
        xData.push(a.name)
        if (a.value === 0) {
          yData.push(a.value + min)
        } else {
          yData.push(a.value)
        }
      })
      let option = {
        // backgroundColor: '#111c4e',
        color: ['#3398DB'],
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'line',
            lineStyle: {
              opacity: 0
            }
          },
          formatter: function (prams) {
            if (prams[0].data === min) {
              return '游客量：0'
            } else {
              return '游客量：' + prams[0].data
            }
          }
        },
        legend: {
          data: ['直接访问', '背景'],
          show: false
        },
        grid: {
          left: '0%',
          right: '0%',
          bottom: '5%',
          top: '7%',
          height: '85%',
          containLabel: true,
          z: 22
        },
        xAxis: [{
          type: 'category',
          gridIndex: 0,
          data: xData,
          axisTick: {
            alignWithLabel: true
          },
          axisLine: {
            lineStyle: {
              color: '#0c3b71'
            }
          },
          axisLabel: {
            show: true,
            color: 'rgb(170,170,170)',
            fontSize: 16
          }
        }],
        yAxis: [{
          type: 'value',
          gridIndex: 0,
          splitLine: {
            show: true,
            lineStyle: {
              color: '#2c385c'
            }
          },
          min: min,
          axisLine: {

          },
          axisLabel: {
            color: 'rgb(170,170,170)',
            formatter: '{value}'
          }
        },
        {
          type: 'value',
          gridIndex: 0,
          min: min,
          splitNumber: 0,
          splitLine: {
            show: true,
            lineStyle: {
              color: '#2c385c'
            }
          },
          axisLine: {
            show: false
          },
          axisTick: {
            show: false
          },
          axisLabel: {
            show: false
          },
          splitArea: {
            show: true,
            areaStyle: {
              color: ['rgba(250,250,250,0.0)']
            }
          }
        }
        ],
        series: [{
          name: '游客量',
          type: 'bar',
          barWidth: '30%',
          xAxisIndex: 0,
          yAxisIndex: 0,
          itemStyle: {
            color: '#50d8d8',
            opacity: 0.6

          },
          data: yData,
          zlevel: 11

        },
        {
          name: '背景',
          type: 'bar',
          barWidth: '30%',
          xAxisIndex: 0,
          yAxisIndex: 0,
          barGap: '-100%',
          data: [1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, 1000],
          itemStyle: {
            normal: {
              color: 'rgba(255,255,255,0.1)'
            }
          },
          zlevel: 9
        }

        ]
      }
      this.chart.setOption(option)
    }
  }
}
</script>
<style lang="less" scoped>
.top_box{
  overflow: hidden;
  margin-top: 14px;
  .tourNumbers{
    float: left;
    height: 130px;
    width: 770px;
    // border: 1px solid #cccccc;
  }
  .chart{
    height: 90%;
  }
  .dayNumbers{
    float: left;
    width: 359px;
    height: 115px;
    border-radius: 4px;
    border: 1px solid rgba(255,255,0,.1);
    margin-left: 30px;
    // opacity: 0.1;
    // background: rgba(0,0,0,0.1);
    background-image: linear-gradient(0deg,rgba(205,205,76, 0.1) 0%,rgba(104, 103, 38, 0.01) 44%,rgba(145, 145, 54, 0.01) 67%,rgba(205,205,76, 0.1) 100%);
    box-sizing: border-box;
    display: flex;
    align-items: center;
    img{
      width: 92px;
      height: 92px;
      margin-right: 27px;
      margin-left: 33px;
    }
    .tips{
      color: #cfce70;
      font-size: 20px;
      margin-bottom: 14px;
    }
    .numbers{
      color: #ffffff;
      font-size: 18px;
      span{
        font-family: DINCompPro-Bold;
        font-size: 48px;
        display: inline-block;
        line-height: 48px;
        margin-right: 10px;
        max-width: 176px;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
      }
    }
  }
}

</style>
