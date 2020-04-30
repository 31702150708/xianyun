<template>
  <div class="container">
    <el-row type="flex" class="row-bg">
      <!-- 左边 -->
      <el-col :span="6">
        <div class="bg-purple">
          <pulldown />
        </div>
      </el-col>

      <!-- 右边 -->
      <el-col :span="18">
        <div class="grid-content bg-purple-light">
          <!-- 输入框 -->
          <el-input placeholder="请输入你想去的地方，比如'广州'" v-model="input3" class="input-with-select">
            <el-button slot="append" icon="el-icon-search" class="el-button"></el-button>
          </el-input>
          <div class="tuijian">
            <span>
              推荐：
              <a href="#">广州</a>
              <a href="#">上海</a>
              <a href="#">北京</a>
            </span>
          </div>

          <div class="nav">
            <div class="strategy">推荐攻略</div>
            <!-- 游记按钮 -->
            <el-button type="primary" icon="el-icon-edit">写游记</el-button>
          </div>
        </div>

        <!-- 分页 -->
        <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="currentPage4"
          :page-sizes="[100, 200, 300, 400]"
          :page-size="100"
          layout="total, sizes, prev, pager, next, jumper"
          :total="400"
        ></el-pagination>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import pulldown from "@/components/post/pullDown.vue";
export default {
  components: {
    pulldown
  },
  data() {
    return {
      input3: "",
      currentPage4: 4
    };
  },
  methods: {
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    }
  },
  mounted() {
    this.$axios({
      url: "/posts/cities"
    }).then(res => {
      console.log(res);
    });
  }
};
</script>

<style scoped lang="less">
.container {
  width: 1000px;
  margin: 0 auto;
  height: 800px;
}
.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}

.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 500px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
// 搜索框样式
.input-with-select {
  border: 4px;
  color: #ffa500;
}
/deep/ .el-input__inner {
  border: 4px solid #ffa500;
}
// 推荐攻略模块.
.nav {
  display: flex;
  border-bottom: 2px solid #eeeeee;
  justify-content: space-between;
  .strategy {
    align-items: center;
    border-bottom: 2px solid #ffa500;
  }
}
</style>