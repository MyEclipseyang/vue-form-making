<template>
  <div>
    <span>{{element.options.content}}</span>
    <el-divider></el-divider>
    <span>总分：{{element.options.totalScore}}</span>
    <template v-if="!element.options.isRelateWithStudent">
      <el-divider></el-divider>
      <div><span>可选分数</span></div>
      <span style="margin-left: 5px;" v-for="(item, index) in element.options.options" :key="index">
              <el-button circle>{{ item.value }}</el-button>
             </span>
    </template>
    <template v-else>
      <el-divider></el-divider>
      <div><span>违纪学生人数（违纪每人次扣{{element.options.violateScoreReduction}}分）</span>
        <el-input
            v-model="element.options.violateStudentNum"
            :style="{width: element.options.width}"
        ></el-input>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "WidgetSingleSelectExamScore",
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
      console.log('WidgetSingleSelectExamScore-getScoreData-element', this.element)
      if(this.element.options.isRelateWithStudent){
        return this.getScoreFormInput()
      }
      return this.getScoreFormButton()
    },
    getScoreFormInput(){
      let totalScore = this.element.options.totalScore
      let violateScoreReduction = this.element.options.violateScoreReduction;
      let violateStudentNum = this.element.options.violateStudentNum
      let result = totalScore - (violateScoreReduction * violateStudentNum)
      if(result < 0 && !this.element.options.isNegativeModel){
        result = 0;
      }
      return {
        key: this.element.model,
        value: result
      }
    },
    getScoreFormButton(){
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