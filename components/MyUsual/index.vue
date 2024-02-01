<template>
  <el-card style="height: 100%;padding: 15px 0 20px 6px;">
    <div slot="header">
      <span style="font-weight: bold">我的常用</span>
    </div>
    <div class="content">
      <div class="content-button">
        <div>
          <el-button icon="el-icon-platform-eleme"><span class="title">文档中心</span><span class="detail">企业全面文档，提高信息共享与协作效率。</span></el-button>
        </div>
      </div>
      <div class="content-button">
        <div>
          <el-button icon="el-icon-platform-eleme"><span class="title">文档中心</span><span class="detail">企业全面文档，提高信息共享与协作效率。</span></el-button>
        </div>
      </div>
      <div class="content-button">
        <div>
          <el-button icon="el-icon-platform-eleme"><span class="title">文档中心</span><span class="detail">企业全面文档，提高信息共享与协作效率。</span></el-button>
        </div>
      </div>
      <div class="content-button">
        <div>
          <el-button icon="el-icon-platform-eleme"><span class="title">文档中心</span><span class="detail">企业全面文档，提高信息共享与协作效率。</span></el-button>
        </div>
      </div>
      <div class="content-button">
        <div>
          <el-button icon="el-icon-platform-eleme"><span class="title">文档中心</span><span class="detail">企业全面文档，提高信息共享与协作效率。</span></el-button>
        </div>
      </div>
    </div>
  </el-card>
</template>

<script>
export default {
  name: "MyUsual"
}
</script>

<style scoped lang="scss">
.content {
  display: grid;
  grid-template-columns: repeat(3, 33%);
  grid-template-rows: repeat(auto-fill, 50px);
  column-gap: 10px;
  row-gap: 15px;
  .content-button{
    .title {
      font-family: "PingFang SC ", "PingFang SC", sans-serif;
      font-weight: 650;
      font-style: normal;
      font-size: 14px;
      color: rgba(0, 0, 0, 0.847);
      line-height: 24px;
    }
    .detail {
      font-family: "PingFang SC ", "PingFang SC", sans-serif;
      font-weight: 400;
      font-style: normal;
      font-size: 12px;
      color: rgba(0, 0, 0, 0.447);
      line-height: 20px;
      margin-left: 10px;
    }
  }
}

</style>
