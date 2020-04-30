<template>
  <div>
    <el-cascader-panel :options="options" :props="{ expandTrigger: 'hover' } " class="hover"></el-cascader-panel>

    <!-- 推荐城市 -->
    <div class="recommend">
      <span>推荐城市</span>
      <img src="http://157.122.54.189:9093/images/pic_sea.jpeg" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: [
        {
          value: "zhinan",
          label: "指南",
          children: [
            {
              value: "shejiyuanze",
              label: "设计原则"
            },
            {
              value: "daohang",
              label: "导航"
            }
          ]
        }
      ]
    };
  },
  mounted() {
    this.$axios({
      url: "/posts/cities"
    }).then(res => {
      const { data } = res.data;
      console.log(data);
    });
  }
};
</script>

<style scoped lang="less" >
/deep/ .el-button {
  width: 250px;
  border-radius: nowrap;
  display: block;
}
.el-button--primary {
  color: black;
  background-color: #ffffff;
  border-color: #eeeeee;
}
// 推荐城市
.recommend {
  span {
    border-bottom: 1px solid #eeeeee;
  }
  img {
    width: 100px;
    height: 100px;
  }
}
</style>