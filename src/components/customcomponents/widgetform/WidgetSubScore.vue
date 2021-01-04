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

<!--    <el-divider>标准</el-divider>-->
<!--    <el-table-->
<!--        :data="element.options.scoreCriterion"-->
<!--        style="width: 100%">-->
<!--      <el-table-column-->
<!--          prop="index"-->
<!--          label="标识"-->
<!--          width="180">-->
<!--      </el-table-column>-->
<!--      <el-table-column-->
<!--          prop="content"-->
<!--          label="内容"-->
<!--          width="180">-->
<!--      </el-table-column>-->
<!--      <el-table-column-->
<!--          prop="scoreNum"-->
<!--          width="180"-->
<!--          label="分数/(每次)">-->
<!--      </el-table-column>-->
<!--      <el-table-column-->
<!--          width="180"-->
<!--          label="模式">-->
<!--        <template slot-scope="scope">-->
<!--          {{ scope.row.isSubMode ? '扣分' : '加分' }}-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column fixed="right" width="200" label="操作">-->
<!--        <template slot-scope="scope">-->
<!--          <el-button-->
<!--              size="mini">查看学生</el-button>-->
<!--          <el-button-->
<!--              size="mini"-->
<!--              type="primary">添加学生</el-button>-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--    </el-table>-->

    <el-divider></el-divider>
    <div><span>获得分数</span>
      <el-input
          v-model="element.options.finalScore"
          :style="{width: element.options.width}"
      ></el-input>
    </div>
<!--    <el-dialog title="添加学生" :visible.sync="dialogFormVisible">-->
<!--      <el-form :model="form">-->
<!--        <el-form-item label="班级" :label-width="formLabelWidth">-->
<!--          <el-input v-model="form.className" autocomplete="off"></el-input>-->
<!--        </el-form-item>-->
<!--        <el-form-item label="姓名" :label-width="formLabelWidth">-->
<!--          <el-input v-model="form.studentName" autocomplete="off"></el-input>-->
<!--        </el-form-item>-->
<!--        <el-form-item label="活动区域" :label-width="formLabelWidth">-->
<!--          <el-select v-model="form.scoreCriterionIndex" placeholder="请选择活动区域">-->
<!--            <el-option v-for="(item, index) in element.options.scoreCriterion"-->
<!--                       :key="index"-->
<!--                       label="区域一" value="shanghai">{{ item.index }}</el-option>-->
<!--          </el-select>-->
<!--        </el-form-item>-->
<!--      </el-form>-->
<!--      <div slot="footer" class="dialog-footer">-->
<!--        <el-button @click="dialogFormVisible = false">取 消</el-button>-->
<!--        <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>-->
<!--      </div>-->
<!--    </el-dialog>-->
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
      formLabelWidth: '120px',
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        scoreCriterionIndex: '',
        className:'',
        studentName:''
      }
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
    handleEdit(index, row) {
      console.log(index, row);
    },
    handleDelete(index, row) {
      console.log(index, row);
    }
  }
}
</script>

<style scoped>

</style>