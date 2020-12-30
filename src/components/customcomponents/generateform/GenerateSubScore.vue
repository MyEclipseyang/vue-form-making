<template>
  <div>
    <span
        :style="{width: widget.options.width, display: 'block'}"
      >{{widget.options.content}}
    </span>
    <template v-if="widget.options.isHaveTotalScore">
      <el-divider/>
      <span>总分：{{widget.options.totalScore}}</span>
    </template>

    <el-divider></el-divider>
    <div><span>获得分数</span>
      <template v-if="widget.options.isHaveTotalScore">
        <el-input-number
            style="margin-left: 5px"
            v-model="widget.options.finalScore"
            :min="0" :max="widget.options.totalScore" :step="0.1">
        </el-input-number>
      </template>
      <template v-else>
        <el-input-number
            style="margin-left: 5px"
            v-model="widget.options.finalScore"
            :min="0" :step="0.1">
        </el-input-number>
      </template>

    </div>
  </div>
</template>

<script>
export default {
  name: "GenerateSubScore",
  props:{
    "widget":{
      required: true
    }
  },
  data(){
    return{

    }
  },
  methods:{
  }
}
</script>

<style scoped>

</style>