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

<!--    <el-divider>标准</el-divider>-->
<!--    <el-table-->
<!--        :data="widget.options.scoreCriterion"-->
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
<!--      <el-table-column label="操作" fixed="right" width="200">-->
<!--        <template slot-scope="scope">-->
<!--          <el-button-->
<!--              size="mini"-->
<!--              @click="handleDetail(scope.$index, scope.row)">查看学生</el-button>-->
<!--          <el-button-->
<!--              size="mini"-->
<!--              type="primary"-->
<!--              @click="handleAdd(scope.$index, scope.row)">添加学生</el-button>-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--    </el-table>-->

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
<!--    <el-dialog title="添加学生" :modal="false" :visible.sync="dialogFormVisible">-->
<!--      <el-form :model="form">-->
<!--        <el-form-item label="班级" :label-width="formLabelWidth">-->
<!--          <el-input v-model="form.className" autocomplete="off"></el-input>-->
<!--        </el-form-item>-->
<!--        <el-form-item label="姓名" :label-width="formLabelWidth">-->
<!--          <el-input v-model="form.studentName" autocomplete="off"></el-input>-->
<!--        </el-form-item>-->
<!--        <el-form-item label="活动区域" :label-width="formLabelWidth">-->
<!--          <el-select v-model="form.scoreCriterionIndex" placeholder="请选择活动区域">-->
<!--            <el-option v-for="(item, index) in widget.options.scoreCriterion"-->
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
  name: "GenerateSubScore",
  props:{
    "widget":{
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
    handleDetail(index, row) {
      console.log(index, row);
    },
    handleAdd(index, row) {
      this.dialogFormVisible = true
      console.log(index, row);
    }
  }
}
</script>

<style scoped>

</style>