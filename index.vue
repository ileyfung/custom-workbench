<template>
  <el-container>
    <el-header>
      <div style="display: flex;justify-content: space-between;">
        <div>
          <h2 style="font-weight: bold">工作台设计</h2>
        </div>
        <div>
          <el-button @click="preview">预览</el-button>
          <el-button>保存</el-button>
          <el-button type="primary">发布</el-button>
        </div>
      </div>
    </el-header>
    <el-container>
      <el-aside>
      <h3 style="font-weight: bold">组件库</h3>
        <div class="components">
          <el-collapse v-model="activated">
            <el-collapse-item name="0">
              <template slot="title">
                <span style="font-weight: bold;">默认组件</span><i class="header-icon el-icon-info"></i>
              </template>
              <div class="components-item">
                <div>
                  <el-button icon="el-icon-platform-eleme" @click="addItem">我的常用</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">待办事项</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">快捷管理</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">系统公告</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">文档中心</el-button>
                </div>
              </div>
            </el-collapse-item>
            <el-collapse-item name="1">
              <template slot="title">
                <span style="font-weight: bold;">业务组件</span><i class="header-icon el-icon-info"></i>
              </template>
              <div class="components-item">
                <div>
                  <el-button icon="el-icon-platform-eleme">核心指标</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">项目实况</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">设备保养</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">日常安全</el-button>
                </div>
                <div>
                  <el-button icon="el-icon-platform-eleme">本月能耗</el-button>
                </div>
              </div>
            </el-collapse-item>
          </el-collapse>

        </div>
      </el-aside>
      <div class="main">
        <grid-layout :layout.sync="layout"
                     :col-num="colNum"
                     :row-height="150"
                     :is-draggable="draggable"
                     :is-resizable="resizable"
                     :vertical-compact="true"
                     :use-css-transforms="true"
                     :responsive="true"
        >
          <grid-item v-for="item in layout"
                     :static="item.static"
                     :x="item.x"
                     :y="item.y"
                     :w="item.w"
                     :h="item.h"
                     :i="item.i"
                     :key="item.i"
                     :auto-size="true"
          >
            <div class="remove" @click="removeItem(item.i)">x</div>
            <my-usual v-if="item.value === 'my-usual'"></my-usual>
          </grid-item>
        </grid-layout>
      </div>
    </el-container>
  </el-container>
</template>

<script>
import { GridLayout, GridItem } from "vue-grid-layout"
import MyUsual from "@/views/custom-workbench/components/MyUsual/index.vue";
export default {
  name: "DiyWork",
  components: {
    MyUsual,
    GridLayout,
    GridItem
  },
  data() {
    return {
      activated: '0',
      layout: [
        // { x: 0, y: 0, w: 2, h: 2, i: "0" ,show: false},
        // { x: 2, y: 0, w: 2, h: 2, i: "1" ,show: false},
        // { x: 4, y: 0, w: 2, h: 2, i: "2" ,show: false},
        // { x: 6, y: 0, w: 2, h: 2, i: "3" ,show: false},
        // { x: 8, y: 0, w: 2, h: 2, i: "4" ,show: false},
      ],
      draggable: true,
      resizable: true,
      index: 0,
      colNum: 6,
    }
  },
  mounted() {
    // this.$gridlayout.load();
    this.index = this.layout.length;
  },
  methods: {
    preview() {
      console.log(this.layout)
      localStorage.setItem("layout", JSON.stringify(this.layout));
      this.$router.push('/preview-workbench')
    },
    addItem: function () {
      // Add a new item. It must have a unique key!
      this.layout.push({
        x: (this.layout.length * 2) % (this.colNum || 12),
        y: this.layout.length + (this.colNum || 12), // puts it at the bottom
        w: 2,
        h: 1,
        i: this.index,
        value: 'my-usual',
      });
      // Increment the counter to ensure key is always unique.
      this.index++;
    },
    removeItem: function (val) {
      const index = this.layout.map(item => item.i).indexOf(val);
      this.layout.splice(index, 1);
    },
  }
}
</script>

<style scoped>
@import url('index.scss');
@import url('grid-layout.scss');
</style>
