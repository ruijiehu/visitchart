<template>
  <card class="shape_row  own-pointer" title="民生" urls="module:people-module">
    <module-title title="景区实时游客量"></module-title>
    <div class="future"><img src="../../../assets/img/people/future.png" alt=""><span>未来社区</span><img src="../../../assets/img/people/more.png" alt=""></div>
    <visitNumbers></visitNumbers>
    <visitPics></visitPics>
  </card>
</template>

<script>
import visitNumbers from './people-visitNumbers'
import visitPics from './people-visitPics'
// import echarts from 'echarts'
require('echarts-wordcloud')
export default {
  components: {
    visitNumbers: visitNumbers,
    visitPics: visitPics
  },
  data () {
    return {}
  },
  mounted () {
  }
}
</script>

<style lang="less" scoped>
@import '~@/styles/index.less';
.future{
  position: absolute;
  top: 22px;
  right: 40px;
  color: #ffffff;
  width: 114px;
  height: 24px;
  border-radius: 12px;
  border: solid 1px #84dbed;
  text-align: center;
  line-height: 23px;
  cursor: pointer;
  font-family: PingFang-SC-Bold;
  font-size: 14px;
  font-weight: normal;
  font-stretch: normal;
  letter-spacing: 0px;
  color: #84dbed;
  vertical-align: middle;
  span{
    margin:0 3px;
  }
  // }
  img{
    margin-top: -2px;
    width: 16px;
    height: 16px;
    vertical-align: middle;
  }
}
</style>
