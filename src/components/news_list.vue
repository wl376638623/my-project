<template>
  <!--增删改查-->
  <div>
    <div style="font-size: 30px;color: salmon">CMS管理</div>
    <!--按钮、表格-->
    <el-card class="box-card">
      <el-button type="success" size="small" @click="add">增加</el-button>
      <el-button type="success" size="small" @click="tuichu">退出</el-button>
      <el-table :data="tableData" stripe>
        <el-table-column prop="date" label="日期" align="center">
        </el-table-column>
        <el-table-column prop="name" label="发布人" align="center">
        </el-table-column>
        <el-table-column prop="address" label="标题" align="center">
        </el-table-column>
        <el-table-column prop="age" label="内容" align="center">
        </el-table-column>
        <el-table-column label="操作" fixed="right" align="center">
          <template slot-scope="scope">
            <el-button type="primary" size="small" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
            <el-button type="danger" size="small" @click="remove(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </el-card>
    <!--弹窗-->
    <el-dialog :title="dialogTitle" width="50%" :visible.sync="iconFormVisible">
      <el-form :inline="true" :model="userInfo" class="demo-form-inline">
        <el-form-item label="发布人">
          <el-input v-model="userInfo.name" placeholder="发布人"></el-input>
        </el-form-item>
        <el-form-item label="日期">
          <el-input v-model="userInfo.date" placeholder="日期"></el-input>
        </el-form-item>
        <el-form-item label="标题">
          <el-input v-model="userInfo.address" placeholder="标题"></el-input>
        </el-form-item>
        <el-form-item label="内容">
          <el-input v-model="userInfo.age" placeholder="内容"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="iconFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="submitUser()">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    name: "news_list",
    data() {
      return {
        iconFormVisible: false,
        userInfo: {},
        dialogTitle: '增加',
        rowIndex: null,
        tableData: [{
          date: '2020-08-11',
          name: '王小虎',
          address: '标题1',
          age: '内容1',
        }, {
          date: '2020-08-11',
          name: '王小虎',
          address: '标题2',
          age: '内容2',
        }, {
          date: '2020-08-11',
          name: '王小虎',
          address: '标题3',
          age: '内容3',
        }, {
          date: '2020-08-11',
          name: '王小虎',
          address: '标题4',
          age: '内容4',
        }],
      };
    },
    created() {
    },
    methods: {
      // 增加
      add() {
        this.dialogTitle = '增加';
        this.userInfo = {};
        this.iconFormVisible = true;
      },
      // 编辑
      handleEdit(index, row) {
        this.dialogTitle = '编辑';
        this.userInfo = row;
        this.iconFormVisible = true;
        this.rowIndex = index;
      },
      // 弹窗确定
      submitUser() {
        if (this.dialogTitle === '编辑') {
          this.tableData.splice(this.rowIndex, 1, this.userInfo);
          this.iconFormVisible = false;
          return;
        }
        this.tableData.splice(0, 0, this.userInfo);
        this.iconFormVisible = false;
      },
      // 删除
      remove(index, row) {
        this.$confirm(`确定删除${row.name}吗?`, '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          type: 'error',
        }).then(() => {
          this.tableData.splice(index, 1);
        });
      },
      tuichu(){
        this.$router.push({
          path: "/login"
        });
      }
    },
    computed: {

    },
  };
</script>

<style scoped>

</style>
