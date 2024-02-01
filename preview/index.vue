<template>
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
        <my-usual v-if="item.value === 'my-usual'"></my-usual>
      </grid-item>
    </grid-layout>
  </div>
</template>

<script>
import { GridLayout, GridItem } from "vue-grid-layout"
import MyUsual from "@/views/custom-workbench/components/MyUsual/index.vue";
export default {
  name: "Preview",
  components: {
    MyUsual,
    GridLayout,
    GridItem
  },
  data() {
    return {
      activated: '0',
      layout: [

      ],
      draggable: false,
      resizable: false,
      index: 0,
      colNum: 6,
    }
  },
  mounted() {
    // this.$gridlayout.load();
    this.layout = JSON.parse(localStorage.getItem("layout"));
    this.index = this.layout.length;
  },
}
</script>

<style scoped>
@import url('../grid-layout.scss');
.main {
  background-color: #f2f6fc;
  width: 100%;
  padding: 10px;
}
</style>
