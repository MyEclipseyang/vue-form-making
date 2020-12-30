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
    <el-form-item label="总分">
      <el-input-number v-model="data.options.totalScore" :min="0" :max="200" :step="1"></el-input-number>
    </el-form-item>
    <template v-if="!data.options.isRelateWithStudent">
      <el-form-item label="分值">
        <draggable tag="ul" :list="data.options.options"
                   v-bind="{group:{ name:'options'}, ghostClass: 'ghost',handle: '.drag-item'}"
                   handle=".drag-item"
        >
          <li v-for="(item, index) in data.options.options" :key="index" >

            <el-input :style="{'width': data.options.showLabel? '90px': '180px' }" size="mini" v-model="item.value"></el-input>
            <el-input style="width:90px;" size="mini" v-if="data.options.showLabel" v-model="item.label"></el-input>
            <i class="drag-item" style="font-size: 16px;margin: 0 5px;cursor: move;"><i class="iconfont icon-icon_bars"></i></i>
            <el-button @click="handleOptionsRemove(index)" circle plain type="danger" size="mini" icon="el-icon-minus" style="padding: 4px;margin-left: 5px;"></el-button>
          </li>
        </draggable>
      </el-form-item>
      <div style="margin-left: 22px;">
        <el-button type="text" @click="handleAddScoreOption">{{$t('fm.actions.addOption')}}</el-button>
      </div>
    </template>
    <el-form-item label="是否与学生关联">
      <el-switch
          v-model="data.options.isRelateWithStudent"
          active-color="#13ce66">
      </el-switch>
    </el-form-item>
    <div v-show="data.options.isRelateWithStudent">
      <el-form-item label="是否允许分数为负数">
        <el-switch
            v-model="data.options.isNegativeModel"
            active-color="#13ce66">
        </el-switch>
      </el-form-item>
      <el-form-item label="违纪学生每人次扣分数">
        <el-input-number v-model="data.options.violateScoreReduction" :min="0" :max="200" :step="1"></el-input-number>
      </el-form-item>
    </div>
  </div>
</template>

<script>
import Draggable from 'vuedraggable'
export default {
  name: "SingleSelectExamScoreConfig",
  components:{
    Draggable
  },
  props: {
    'data':{
      required: true
    }
  },
  methods:{
    handleOptionsRemove(index){
      this.data.options.options.splice(index, 1)
    },
    handleAddScoreOption(){
      this.data.options.options.push({value: 0})
    },
  }
}
</script>

<style scoped>

</style>