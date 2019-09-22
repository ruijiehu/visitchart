<template>
 <div class="bottom_box">
      <div class="section">
        <module-title title="客源地"></module-title>
        <div class="chart1" ref="chart1"></div>
      </div>
      <div class="section">
        <module-title title="景区消费分析"></module-title>
        <ul class="consume">
          <li>
            <img src="../../../assets/img/people/tourist_eat.png" alt="">
            <span>餐饮</span>
            <span>12.34%</span>
          </li>
          <li>
            <img src="../../../assets/img/people/tourist_tickets.png" alt="">
            <span>门票</span>
            <span>12.34%</span>
          </li>
          <li>
            <img src="../../../assets/img/people/tourist_stay.png" alt="">
            <span>住宿</span>
            <span>12.34%</span>
          </li>
          <li>
            <img src="../../../assets/img/people/tourist_go.png" alt="">
            <span>交通</span>
            <span>12.34%</span>
          </li>
          <li>
            <img src="../../../assets/img/people/tourist_other.png" alt="">
            <span>其他</span>
            <span>12.34%</span>
          </li>
        </ul>
      </div>
      <div class="section">
        <module-title title="景区舆情监测"></module-title>
        <div class="section_box">
          <div class="cloud-container" ref="chart2"></div>
          <div class="evaluate">
            <div class="good">
              <img src="../../../assets/img/people/eva_1.png" alt="" class="good_ico">
              <div class="good_react">
                <div class="rect_top"><span class="y1">正面</span><span>48.4%</span></div>
                <div class="rect_bottom"><span class="yb1"></span><span></span></div>
              </div>
            </div>
            <div class="good">
              <img src="../../../assets/img/people/eva_2.png" alt="" class="good_ico">
              <div class="good_react">
                <div class="rect_top"><span class="y2">中性</span><span>48.4%</span></div>
                <div class="rect_bottom"><span class="yb2"></span><span></span></div>
              </div>
            </div>
            <div class="good">
              <img src="../../../assets/img/people/eva_3.png" alt="" class="good_ico">
              <div class="good_react">
                <div class="rect_top"><span class="y3">负面</span><span>48.4%</span></div>
                <div class="rect_bottom"><span class="yb3"></span><span></span></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
// import RunNum from '@/components/run-num'
import echarts from 'echarts'
require('echarts-wordcloud')
export default {
  components: {
  },
  data () {
    return {}
  },
  mounted () {
    this.initChart1()
    this.initChart2()
  },
  methods: {
    initChart1 () {
      this.chart = echarts.init(this.$refs.chart1)
      var m2R2Data = [
        { value: 335, legendname: '江苏省', name: '江苏省 335' },
        { value: 310, legendname: '浙江省', name: '浙江省 310' },
        { value: 234, legendname: '上海市', name: '上海市 234' },
        { value: 154, legendname: '福建省', name: '福建省 154' },
        { value: 335, legendname: '其他', name: '其他     355' }
      ]

      let option = {
        tooltip: {
          trigger: 'item',
          formatter: function (parms) {
            var str = parms.marker + '' + parms.data.legendname + '</br>' +
            '数量：' + parms.data.value + '</br>' +
            '占比：' + parms.percent + '%'
            return str
          }
        },
        legend: {
          type: 'plain',
          orient: 'vertical',
          left: '50%',
          align: 'left',
          top: 'middle',
          itemWidth: 14,
          textStyle: {
            color: '#fff'
          },
          height: 250
        },
        color: ['#be375d', '#7138db', '#3890db', '#3e8e4f', '#233f91'],
        series: [
          {
            name: '',
            type: 'pie',
            center: ['25%', '50%'],
            radius: ['40%', '65%'],
            clockwise: false, // 饼图的扇区是否是顺时针排布
            data: m2R2Data,
            label: {
              normal: {
                show: false
              }
            }
          }
        ]
      }
      this.chart.setOption(option)
    },
    initChart2 () {
      this.chart = echarts.init(this.$refs.chart2)
      let options = {
        tooltip: {
          show: true
        },
        series: [{
          type: 'wordCloud',
          gridSize: 10,
          rotationRange: [0, 0],
          sizeRange: [18, 30],
          width: '100%',
          height: '100%',
          textStyle: {
            normal: {
              color: function () {
                return 'rgb(' + [
                  Math.round(Math.random() * 100),
                  Math.round(Math.random() * 100),
                  Math.round(Math.random() * 255)
                ].join(',') + ')'
              }
            },
            emphasis: {
              shadowBlur: 10,
              shadowColor: '#333'
            }
          },
          data: [{
            name: ' 没有',
            value: 30
          },
          {
            name: ' 屏幕',
            value: 24
          },
          {
            name: ' 不错',
            value: 21
          },
          {
            name: ' 可以',
            value: 19
          },
          {
            name: ' 可以',
            value: 19
          },
          {
            name: ' 可以',
            value: 19
          },
          {
            name: ' 可以',
            value: 19
          },
          {
            name: ' 可以',
            value: 19
          }
          ]
        }] }
      this.chart.setOption(options)
    }
  }
}
</script>
<style lang="less" scoped>
.bottom_box{
  display: flex;
  margin-top: 10px;
  .section{
    &:nth-child(3){
      margin-left: 54px;
    }
    flex: 1;
    .chart1{
      height: 150px;
      margin-top: 14px;
    }
    .consume{
      width: 110%;
      margin:0;
      padding: 0;
      margin-top: 32px;
      li{
        float: left;
        overflow: hidden;
        width: 56px;
        text-align: center;
        margin-right: 20px;
        img{
          display: inline-block;
          width: 41px;
          height: 41px;
          margin:0 auto 24px;
        }
        span{
          width: 100%;
          text-align: center;
          display: inline-block;
          color: #18bcdf;
          &:nth-child(3){
            color: #fff;
            margin-top: 15px;
          }
        }
      }
    }
    .section_box{
      width: 364px;
      height: 134px;
      background-image: linear-gradient(0deg,rgba(1,180,255, .1) 0%,rgba(19,49,169, .1) 100%);
      // opacity: 0.25;
      margin-top: 20px;
      .cloud-container{
        height: 150px;
        width: 200px;
        float: left;
      }
      .evaluate{
        float: left;
        width: 164px;
        color: #fff;
        .good{
          height: 42px;
          &:nth-child(1){
            margin-top: 10px;
          }
          .good_ico{
            display: inline-block;
            width: 21px;
            height: 21px;
            vertical-align: middle;
          }
          .good_react{
            vertical-align: middle;
            display: inline-block;
            width: 80%;
            .rect_top{
              display: flex;
              justify-content: space-between;
              font-size: 14px;
              span{
                display: inline-block;
              }
              .y1{
                color: #2abda7;
              }
               .y2{
                color: #c2b863;
              }
               .y3{
                color: #cf3240;
              }
            }
            .rect_bottom{
              position: relative;
              margin-top: 5px;
              height: 8px;
              span{
                position: absolute;
                top: 0;
                left: 0;
                width: 100%;
                height: 8px;
                background-color: #1a2f61;
                &:nth-child(1){
                  width: 30%;
                  background-color: #50d8d8;
                  z-index: 1;
                }
                &.yb1{
                background-color: #2abda7;
              }
               &.yb2{
                background-color: #c2b863;
              }
               &.yb3{
                background-color: #cf3240;
              }
              }

            }
          }

        }
      }
    }
  }
}

</style>
