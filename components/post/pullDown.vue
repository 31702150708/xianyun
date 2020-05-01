<template>
  <div>
    <div class="liebiao">
      <ul>
        <li>
          热门城市
          <i class="el-icon-arrow-right"></i>
        </li>
        <li>
          热门城市
          <i class="el-icon-arrow-right"></i>
        </li>
        <li>
          热门城市
          <i class="el-icon-arrow-right"></i>
        </li>
        <li>
          热门城市
          <i class="el-icon-arrow-right"></i>
        </li>
      </ul>
    </div>

    <!-- 推荐城市 -->
    <div class="recommend">
      <span class="tuijian">推荐城市</span>
      <a href="#">
        <img src="http://157.122.54.189:9093/images/pic_sea.jpeg" />
      </a>
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
          label: "指南"
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
// 列表
.liebiao {
  margin-top: 15px;
  ul {
    li {
      width: 100%;
      height: 40px;
      line-height: 40px;
      border: 1px solid #eeeeee;
      padding-left: 20px;
      font-size: 14px;
    }
  }
}
// 推荐城市
.recommend {
  span {
    display: block;
    width: 100%;
    height: 40px;
    line-height: 40px;
    border-bottom: 1px solid #eeeeee;
    padding-top: 15px;
  }
  img {
    display: flex;
    width: 100%;
    height: 100%;
    margin-top: 10px;
  }
}
</style>