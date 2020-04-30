<template>
  <div class="hotel-index">
    <el-breadcrumb separator-class="el-icon-arrow-right" class="hotel-bread">
      <el-breadcrumb-item>酒店</el-breadcrumb-item>
      <el-breadcrumb-item>酒店预订</el-breadcrumb-item>
    </el-breadcrumb>
    <el-form :inline="true" :model="formInline" class="demo-form-inline">
      <el-form-item>
        <el-autocomplete class="el-autocomplete"></el-autocomplete>
      </el-form-item>
      <el-form-item>
        <el-date-picker
          type="daterange"
          range-separator="-"
          start-placeholder="入住时间"
          end-placeholder="离店时间"
          :picker-options="pickerOptions"
        ></el-date-picker>
      </el-form-item>
      <el-form-item>
        <div class="hotel-people">
          <el-popover placement="bottom" width="300" trigger="click">
            <el-row type="flex" align="middle">
              <span class="hotel-select-item">每间</span>
              <el-select placeholder="2成人" size="mini" class="select-item" @change="addlabel('成人')">
                <el-option v-for="item in 7" :key="item" :label="item" :value="item"></el-option>
              </el-select>
              <el-select placeholder="0儿童" size="mini" class="select-item" @change="addlabel('儿童')">
                <el-option v-for="item in 4" :key="item + 10" :label="item" :value="item"></el-option>
              </el-select>
            </el-row>
            <div class="btn-col"></div>
            <el-row type="flex" justify="end">
              <el-button type="primary" size="mini" @click="addContentToInput">确定</el-button>
            </el-row>
            <div slot="reference" ref="personal">
              <el-input placeholder="请输入内容" suffix-icon="el-icon-user" readonly="readonly"></el-input>
            </div>
          </el-popover>
        </div>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="queryPrice">查看价格</el-button>
      </el-form-item>
    </el-form>
    <el-row class="hotel-option-row">
      <el-col :span="14" class="hotel-area">
        <el-row class="search-options">
          <el-row class="option-row">
            <el-col :span="3">区域：</el-col>
            <el-col :span="21" :class="{'hidden-all': isSpread}">
              <div class="scenics-box" :class="{limitHeight: isSpread}">
                <span class="location-budget" v-for="(item) in scenics" :key="item.id">{{item.name}}</span>
              </div>
              <div @click="spreadContent">
                <i class="el-icon-d-arrow-right"></i>
                等个区域
              </div>
            </el-col>
          </el-row>
          <el-row class="option-row">
            <el-col :span="3">
              均价：
              <el-tooltip
                class="item"
                effect="dark"
                content="等级均价由平日价格计算得出，节假日价格会有上浮"
                placement="top-start"
              >
                <span class="hotelTool">?</span>
              </el-tooltip>
            </el-col>
            <el-col :span="21">
              <el-row>
                <el-col :span="6">
                  <el-tooltip
                    class="item"
                    effect="dark"
                    content="等级评定是针对房价，设施和服务等各方面水平的综合评估"
                    placement="bottom-start"
                  >
                    <span>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <span class="price-budget">¥332</span>
                    </span>
                  </el-tooltip>
                </el-col>
                <el-col :span="7">
                  <el-tooltip
                    class="item"
                    effect="dark"
                    content="等级评定是针对房价，设施和服务等各方面水平的综合评估"
                    placement="bottom-start"
                  >
                    <span>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <span class="price-budget">¥521</span>
                    </span>
                  </el-tooltip>
                </el-col>
                <el-col :span="10">
                  <el-tooltip
                    class="item"
                    effect="dark"
                    content="等级评定是针对房价，设施和服务等各方面水平的综合评估"
                    placement="bottom-start"
                  >
                    <span>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <i class="iconfont iconhuangguan"></i>
                      <span class="price-budget">¥768</span>
                    </span>
                  </el-tooltip>
                </el-col>
              </el-row>
            </el-col>
          </el-row>
        </el-row>
      </el-col>
      <!-- 地图 -->
      <el-col :span="10" v-loading="loading">
        <div id="container"></div>
      </el-col>
    </el-row>
    <!-- 过滤菜单 -->
    <div>
      <HotelFilter :enterTime="enterTime" :leftTime="leftTime" />
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="less" scoped>
.hotel-index {
  width: 1000px;
  min-width: 1000px;
  min-height: 900px;
  margin: 0 auto;
}
.hotel-bread {
  padding: 20px 0;
}
.hotel-select {
  position: absolute;
  bottom: -134px;
  left: 0;
  width: 300px;
  height: 123px;
  z-index: 99;
}
.hotel-select-item {
  flex: 1;
}
.hotel-people {
  position: relative;
}
.select-item {
  width: 93px;
  padding: 0 5px;
}
/deep/ .el-card__body {
  padding: 12px;
}
.btn-col {
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px solid #ddd;
}
.hotel-option-row {
  min-height: 260px;
  margin-bottom: 20px;
  .hotel-area {
    padding: 0 5px;
  }
}
.option-row {
  margin-bottom: 20px;
  color: #666;
  font-size: 14px;
}
.scenics-box {
  .location-budget {
    margin-right: 1em;
    padding: 0 2px;
    border-radius: 4px;
    display: inline-block;
    cursor: pointer;
  }
}
.limitHeight {
  max-height: 3em;
  overflow: hidden;
}
.option-row .hidden-all .el-icon-d-arrow-right {
  transform: rotate(90deg);
}
.option-row .el-icon-d-arrow-right {
  color: #f90;
  transform: rotate(270deg);
  cursor: pointer;
}
.hotelTool {
  display: inline-block;
  position: relative;
  top: -2px;
  width: 20px;
  height: 20px;
  background-color: #cccccc;
  border-radius: 50%;
  font-size: 10px;
  text-align: center;
  line-height: 20px;
  color: #fff;
  font-weight: 700;
}
.iconhuangguan {
  color: #f90;
}
.iconhuangguan::before {
  content: "\e7aa";
}
.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
}
.price-budget {
  margin-left: 5px;
}
#container {
  width: 420px;
  height: 260px;
}
</style>