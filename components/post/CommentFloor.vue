<template>
  <div>
    <div class="comment-floor">
      <!-- 组件在这个位置自己调用自己 -->
      <!-- <commentFloor /> -->

      <div class="floor-top">
        <div class="user">
          <!-- <span>{{count}}</span> -->
          <em>天青茯苓</em>
          <span>2020/4/3</span>
        </div>
        <!-- 点击回复按钮时候触发父组件传递过来的回复函数 -->
      </div>
      <div class="content">这个是什么</div>
      <span class="reply" @click="handleReply()">回复</span>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import { log } from "util";
export default {
  name: "commentFloor",
  data() {
    return {
      isShow: false,
      moment
    };
  },
  props: ["data", "count"],
  methods: {
    // 组件内部的回复的事件
    handleReply(data) {
      // 触发父组件传递过来的reply函数
      // this.$emit("reply", data);
    }
  }
};
</script>


<style scoped lang="less">
.comment-floor {
  margin-bottom: 20px;
  border: 1px #ddd solid;
  padding: 2px;
  font-size: 13px;
  .reply {
    margin-left: 600px;
  }

  .floor-top {
    display: flex;
    justify-content: space-between;
    padding: 20px 5px;

    span {
      font-size: 12px;
      color: #999;
      margin-right: 5px;
    }
    em {
      margin-right: 5px;
    }
  }

  .content {
    padding: 20px 5px;
    padding-top: 0;
  }
}
</style>