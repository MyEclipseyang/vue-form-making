<template>
  <div>
    <span
        :style="{ width: element.options.width,
                  display: 'block'
                }">
      {{element.options.content}}
    </span>

    <template v-if="element.options.isHaveTotalScore">
      <el-divider></el-divider>
      <span>总分：{{element.options.totalScore}}</span>
    </template>

    <el-divider></el-divider>
    <div><span>获得分数</span>
      <el-input
          v-model="element.options.finalScore"
          :style="{width: element.options.width}"
      ></el-input>
    </div>
  </div>
</template>

<script>
export default {
  name: "WidgetSubScore",
  props:{
    "element":{
      required: true
    }
  },
  data(){
    return{

    }
  },
  methods:{
    // 正确计算出该题目组件的分数
    getScoreData(){
      console.log('WidgetSubScore-getScoreData-element', this.element)
      return {
        key: this.element.model,
        value: this.element.options.finalScore
      }
    },
  }
}
</script>

<style scoped>

</style>