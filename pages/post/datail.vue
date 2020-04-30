<template>
  <div class="contianer">
    <el-col :span="17">
      <div class="Left_layout">
        <span>旅游攻略/攻略详情</span>
        <h6>塞班贵？一定是你的打开方式不对！6000块玩转塞班</h6>
        <!-- 横线 -->
        <div class="box"></div>
        <!--攻略 阅读 -->
        <div class="ntroduction_reading">
          <div>
            <span>攻略2019-05-22 10:57</span>
            <span>阅读：15214</span>
          </div>
        </div>
        <!-- 标题 -->
        <div class="Title">
          <span>大家对塞班岛总存在着这样的误解，知道它是美属地盘，就理所当然地觉得这里的花费一定很高，花费高有高的玩法，那如果只有6000块的预算呢？要怎么玩？关于旅行这件事，我们要让钱花得更有道理，收下这份攻略，带你6000块花式玩转塞班。</span>
          <!-- 图片 -->
          <div class="image">
            <img src="../../assets/23.png" alt />
            <span>图：塞班岛。 by第5季旅游</span>
          </div>
        </div>
        <h5></h5>
        <!-- 内容 -->
        <div class="content">
          <div>
            <h5>一、怎样用6000块玩转塞班?</h5>
            <span>大多数出境游客人不做预算或最终花费远远超出预算，对预算的合理分配对控制我们旅行的花费就很重要了，如何只花6000块玩转塞班岛，对预算超支say no？下面从5个方面来为您一一解读：机票+酒店、岛上交通、玩乐项目、吃以及购买纪念品</span>
            <img src="../../assets/6@2x.png" alt />
            <p class="box1">
              <img src="../../assets/23.png" alt />
            </p>
            <span>
              怎样去塞班？可以转机也可以直飞，转机大多会从韩国转，提前蹲守能买到韩国飞塞班的特价机票，2000以下就能入手，加上国内飞韩国的机票来回塞班得5000+，还没算上在塞班的住宿费用，转机还有中途等待的时间，光花在路途上的时间就比直飞要多上一倍甚至更多，转乘奔波劳累，非联程票还要担心行李托运问题，所以建议大家有直飞还是尽量选择直飞。
              在酒店上，旅途中我们呆在酒店的时间远比在外游玩的时间少，酒店干净整洁基本就能满足我们休息的需求，塞班不是个享受酒店的地方而且还真不能跟国内星级酒店等位比较，所以不建议大家花过多的钱在塞班的酒店体验上。
              怎样在机票酒店上获得最高性价比的体验？ 直飞塞班的航班一般和酒店一起打包成机票+酒店套餐，价格要比单定机票、酒店要更加便捷实惠，往往3千多就能把机票和酒店一键搞定。
            </span>
          </div>
        </div>
        <!-- 评论 -->
        <div class="comment">
          <div class="comment_in">
            <div>
              <img src="../../assets/dz.png" alt />
              <img src="../../assets/232.png" alt />
            </div>
            <span>评论(100)</span>
            <span>分享(100)</span>
          </div>
          <!-- 发表 -->
          <div class="form">
            <span>评论</span>
            <div class="glyuan">回复管理员</div>
            <el-input
              type="textarea"
              :autosize="{ minRows: 2, maxRows: 6}"
              placeholder="说点什么吧"
              v-model="textarea2"
            ></el-input>
            <div class="box3">
              <el-button type="primary">主要按钮</el-button>
            </div>
            <!-- 图片上传 -->
            <div class="box4">
              <el-upload
                action="https://jsonplaceholder.typicode.com/posts/"
                list-type="picture-card"
                :on-preview="handlePictureCardPreview"
                :on-remove="handleRemove"
              >
                <i class="el-icon-plus"></i>
              </el-upload>
            </div>
            <el-dialog :visible.sync="dialogVisible">
              <img width="100%" :src="dialogImageUrl" alt />
            </el-dialog>
          </div>
          <!--  评论-->
          <div>
            <div class="comment1">
              <div class="comment-top">
                <div class="user">
                  <img src="../../assets/6@2x.png" />
                  <div class="user-info">
                    <p>天青茯苓</p>
                    <!-- moment().fromNow 就是显示距离到当前的时间 -->
                    <span>一天前</span>
                  </div>
                </div>
              </div>
              <div class="content">那个是什么</div>
              <span class="reply" @click="handleReply">回复</span>
              <!-- 递归组件 -->
              <CommentFloor />
            </div>
          </div>
        </div>
        <!-- 分页 -->
        <div class="paging">
          <el-pagination
            @size-change="handleSizeChange"
            @current-change="handleCurrentChange"
            :current-page="currentPage4"
            :page-sizes="[100, 200, 300, 400]"
            :page-size="100"
            layout="total, sizes, prev, pager, next, jumper"
            :total="400"
          ></el-pagination>
        </div>
      </div>
    </el-col>

    <!-- 右边相关攻略 -->
    <el-col :span="7">
      <div class="related_strategies">
        <span>相关攻略</span>
      </div>

      <div class="related_biaoti">
        <div class="related_r">
          <img src="../../assets/232.png" alt />
        </div>
        <div class="related_l">
          <span>小黑屋一日</span>
          <p>2020-04-13 2:02 阅读 60</p>
        </div>
      </div>
      <div class="related_biaoti">
        <div class="related_r"></div>
        <div class="related_l">
          <span>小黑屋一日</span>
          <p>2020-04-13 2:02 阅读 60</p>
        </div>
      </div>
    </el-col>
  </div>
</template>

<script>
moment.locale("zh-CN");
import moment from "moment";
import CommentFloor from "@/components/post/CommentFloor.vue";
export default {
  components: {
    CommentFloor
  },
  data() {
    return {
      textarea2: "",
      dialogImageUrl: "",
      dialogVisible: false,
      currentPage1: 5,
      currentPage2: 5,
      currentPage3: 5,
      currentPage4: 4
    };
  },
  methods: {
    // 图片上传组件
    handleRemove(file, fileList) {
      console.log(file, fileList);
    },
    // 图片上传组件
    handlePictureCardPreview(file) {
      this.dialogImageUrl = file.url;
      this.dialogVisible = true;
    },
    // 分页组件
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    // 分页组件
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    // 回复
    handleReply() {}
  }
};
</script>

<style scoped lang="less">
.contianer {
  height: 4000px;
  width: 1000px;
  margin: 0 auto;
  .related_strategies {
    height: 40px;
    margin-top: 25px;
    border-bottom: 1px solid rgb(179, 179, 179);
    margin-left: 30px;
    span {
      display: block;
      margin-bottom: 10px;
    }
  }
  .related_biaoti {
    overflow: hidden;
    height: 100px;
    border-bottom: 1px solid rgb(179, 179, 179);
    margin-left: 30px;
    .related_r {
      float: left;

      img {
        width: 100px;
        height: 80px;
      }
    }
    .related_l {
      span {
        margin-top: 5px;
        display: block;
      }
      p {
        display: block;
        font-size: 14px;
        color: rgb(104, 104, 104);
        margin-top: 50px;
      }
    }

    span {
      // float:right;
      display: block;
      margin-bottom: 10px;
    }
    p {
      margin-top: 20px;
      margin-bottom: 40px;
    }
  }
  .Left_layout {
    // 标题
    margin-top: 20px;
    // 标题大小
    h6 {
      margin-top: 20px;
      font-size: 36px;
    }
    // 横线
    .box {
      border-bottom: 1px solid rgb(179, 179, 179);
      margin: 25px 0px 25px 0;
    }
    .Title {
      height: 600px;
      .image {
        margin-top: 20px;
        width: 710px;
        height: 340px;
        img {
          margin-top: 20px;

          width: 100%;
        }
      }
    }
    // 图片

    // 攻略阅读
    .ntroduction_reading {
      margin-top: 20px;
      margin-left: 420px;
      color: rgb(163, 163, 163);
    }
    // 图片标题
  }
  // <!-- 内容 -->
  .content {
    margin-top: -50px;
    h5 {
      font-size: 28px;
    }
    .box1 {
      margin-top: 50px;
      margin-bottom: 50px;
      img {
        height: 510px;
        width: 100%;
      }
    }
  }
  // 评论
  .comment {
    // 评论分享
    .comment_in {
      margin-top: 30px;
      height: 60px;
      margin-left: 280px;
      img {
        margin-left: 25px;
        margin-bottom: 10px;
      }
      span {
        margin-left: 10px;
      }
    }
    .form {
      height: 255px;
      margin-top: 40px;

      span {
        font-size: 20px;
      }
      .glyuan {
        margin-top: 30px;
        margin-bottom: 10px;
      }
      .box3 {
        float: right;

        margin-top: 10px;
        height: 60px;
      }
      .box4 {
        margin-top: 20px;
      }
    }
  }
  // 评论列表
  .comment1 {
    margin-top: 60px;
    padding: 20px;
    border: 1px #eee solid;
    font-size: 13px;
    margin-bottom: 60px;
    .reply {
      margin-left: 600px;
    }
  }
  .comment-top {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;

    .reply {
      font-size: 12px;
    }
    .user {
      display: flex;
      align-items: center;
      img {
        display: block;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        margin-right: 5px;
      }

      span {
        color: #999;
        font-size: 12px;
      }
    }
  }

  .content {
    margin-top: 20px;
  }

  .publish {
    position: fixed;
    width: 100%;
    left: 0;
    bottom: 0;
    padding: 20px;
    box-sizing: border-box;
    background: #fff;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;

    .textarea {
      background: #eee;
      border-radius: 50px;
      padding: 5px 15px;
    }

    .ative {
      height: 82px !important;
      border-radius: 8px;
    }

    .submit {
      margin-left: 5px;
      padding: 3px 10px;
      color: #fff;
      background: red;
      border-radius: 50px;
      font-size: 12px;
      flex-shrink: 0;
    }
  }
}
</style>