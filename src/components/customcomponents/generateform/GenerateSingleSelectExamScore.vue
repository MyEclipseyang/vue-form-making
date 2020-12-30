<template>
  <div>
    <span>{{widget.options.content}}</span>
    <el-divider></el-divider>
    <span>总分：{{widget.options.totalScore}}</span>

    <template v-if="!widget.options.isRelateWithStudent">
      <el-divider></el-divider>
      <div><span>可选分数</span></div>
      <span style="margin-left: 5px;" v-for="(item, index) in widget.options.options" :key="index">
            <el-button :type="widget.options.finalScore === item.value ? 'success' : ''"
                       @click="setFinalScore(item.value)" circle>{{ item.value }}
            </el-button>
        </span>
    </template>
    <template v-else>
      <el-divider></el-divider>
      <div><span>违纪学生人数（违纪每人次扣{{widget.options.violateScoreReduction}}分）</span>
        <el-input
            v-model="widget.options.violateStudentNum"
            :style="{width: widget.options.width}"
        ></el-input>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "GenerateSingleSelectExamScore",
  props: {
    "widget": {
      required: true
    }
  },
  data() {
    return {
    }
  },
  methods:{
    setFinalScore(scoreNum){
      console.log('GenerateSingleSelectExamScore-setFinalScore-element', this.widget, scoreNum)
      this.widget.options.finalScore = scoreNum;
    }
  }

}
</script>

<style scoped>

</style>