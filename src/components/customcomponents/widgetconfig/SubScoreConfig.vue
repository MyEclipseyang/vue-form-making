<template>
  <div>
    <el-form-item label="题目内容">
      <el-input
          type="textarea"
          :rows="5"
          placeholder="请输入内容"
          v-model="data.options.content">
      </el-input>
    </el-form-item>
    <el-form-item label="该考核题目是否有总分">
      <el-switch
          v-model="data.options.isHaveTotalScore"
          active-color="#13ce66">
      </el-switch>
    </el-form-item>
<!--    <el-form-item label="得分标准">-->
<!--      <div style="border: solid #f4f4f4 1px; padding: 5px;" v-for="(item, index) in data.options.scoreCriterion" :key="index">-->
<!--        <div>-->
<!--          <span>标识：{{ item.index }}</span>-->
<!--          <el-button @click="handleOptionsRemove(index)"-->
<!--                     circle plain type="danger"-->
<!--                     size="mini" icon="el-icon-minus"-->
<!--                     style="padding: 4px;margin-left: 5px;"/>-->
<!--        </div>-->
<!--        <div>-->
<!--          <span>内容</span>-->
<!--          <el-input type="textarea"-->
<!--                    :rows="5" :placeholder="item.tip" v-model="item.content"/>-->
<!--        </div>-->
<!--        <div>-->
<!--          <span>分值</span>-->
<!--          <el-input v-model="item.scoreNum"/>-->
<!--        </div>-->
<!--        <div>-->
<!--          <span>是否为减分</span>-->
<!--          <el-switch-->
<!--              style="margin-left: 5px;"-->
<!--              v-model="item.isSubMode"-->
<!--              active-color="#13ce66">-->
<!--          </el-switch>-->
<!--        </div>-->
<!--      </div>-->
<!--      <div style="margin-left: 22px;">-->
<!--        <el-button type="text" @click="handleAddScoreOption">添加标准</el-button>-->
<!--      </div>-->
<!--    </el-form-item>-->
    <el-form-item label="总分" v-if="data.options.isHaveTotalScore">
      <el-input-number v-model="data.options.totalScore" :min="0" :step="1"></el-input-number>
    </el-form-item>
  </div>
</template>

<script>
export default {
  name: "SubScoreConfig",
  props:{
    'data':{
      required: true
    }
  },
  methods:{
    handleAddScoreOption(){
      let index = this.data.options.scoreCriterion.length + 1
      this.data.options.scoreCriterion.push(
          {
            index: '标准' + index,
            content: '',
            tip: '请输入标准内容',
            scoreNum: 0,
            isSubMode: false
          }
      )
    },
    handleOptionsRemove(index){
      this.data.options.scoreCriterion.splice(index, 1)
      this.data.options.scoreCriterion.forEach((item, index) =>{
        item.index = '标准' + ( index + 1 )
      })
    },
  }
}
</script>

<style scoped>

</style>