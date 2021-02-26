<template>
  <div id="app">
    <!-- <h2>测试看下,,成功了没有</h2> -->

    <hr />
    <h1>ToDo APP</h1>
    <hr />

    <!-- 添加项目组 -->
    <!-- <p class="li-p"><span class="el-alert__icon el-icon-info"> </span>目前没有活动</p> -->
    <!--  v-for="(item, i) in liss" :key="i"  -->

    <!--  这里展示 --- 数据 -->
    <div>
      <!-- 表头样式 -->
      <el-table :data="liss" style="width: 100%">
        <!--  表头的内容 -->
        <el-table-column label="内容" width="180" prop="aaa">  </el-table-column>
        <el-table-column label="日期" width="180" prop="bbb" :formatter = "row => typeof row.bbb === 'string' ? row.bbb :row.bbb.toString() ">  </el-table-column>

        <!--  后面的图标  第一个 -->
        <el-table-column label="删除">
          <template>
            <el-button  type="danger" @click="handleDelete()">删除</el-button>
          </template>
        </el-table-column>

        <!-- 后面图标第二个 -->
        <!-- <el-table-column label="完成">
          <template>
            <el-button  @click="handleEdit()">编辑</el-button>
          </template>
        </el-table-column> -->
      </el-table>
    </div>

    <!--  提醒事项  -->
    <div class="count">
      <span> 已完成事项: </span>
      <span class="count-spp"> 总事项: </span>
    </div>

    <!-- 添加事项 -->
    <div class="events">
      <div class="events-one">
        <span> 要做的事: </span>
        <el-input
          v-model="input"
          placeholder="请输入内容"
          class="inputel"
          style="width: 210px"
        ></el-input>
      </div>

      <div class="events-two">
        <span> 日期 : </span>
        <div class="block">
          <el-date-picker v-model="value1" type="date" placeholder="选择日期">
          </el-date-picker>
        </div>
      </div>
    </div>

    <!-- 图标,,,点击添加事件 -->
    <div>
      <el-button
        type="primary"
        icon="el-icon-circle-plus-outline"
        circle
        @click="btn"
      ></el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",

  methods: {
    btn() {
      // console.log("测试一下");
      // 我这里将  input,,,input3的都要添加到数组里面去,,,,但是要有一点,要注意是,,,,添加到数组的开头,,,还是尾巴处
      this.liss.push({bbb: this.value1,aaa: this.input }),
        (this.input = ""),
        (this.value1 = ""),
        console.log(this.liss);

        //   事项:::看看
    },
  },

  data() {
    return {
      // 这里有三种数,一个是   输入的,,,一个是日期 ,,,,别一个是数据,将添加 的加入进来

      // 输入框 ---事情
      input: "",

      liss: [],

      // 日期
      value1: "",
      currentRow: null,
      disabledDate(time) {
        return time.getTime() > Date.now();
      },


      // 事项数
      tag:'',
      tagg:' '
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
  margin-top: 25px;
}

.li-p {
  height: 37px;
  background-color: #f4f4f5;
  text-align: center;
  line-height: 37px;
  margin-top: 28px;
  font-size: 13px;
  color: #909399;
}
.count {
  height: 21px;
  text-align: center;
  margin-top: 10px;
}
.count-spp {
  margin-left: 75px;
}

/* 输入框  */
.events {
  margin-top: 10px;
  font-size: 16px;

  text-align: center;
}
.events-one {
  display: inline-block;
}
.events-two {
  display: inline-block;
}
.block {
  display: inline-block;
}

.sp {
  /* float: left; */
  display: inline-block;
}
</style>
