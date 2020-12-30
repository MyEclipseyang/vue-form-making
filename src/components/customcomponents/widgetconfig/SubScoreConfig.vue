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
  }
}
</script>

<style scoped>

</style>