<template>
  <div>
    <!-- 版本选择框 -->
    <div class="versions" v-if="$page.relativePath.includes('versions')">
      <el-select v-model="version" placeholder="请选择" size="mini" :class="{'select':version!==''}" @change="versionChange">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value"
        >
        </el-option>
      </el-select>
    </div>
    <!-- 侧边栏导航 -->
    <div
      class="group"
      v-for="item in Object.keys($site.themeConfig.sidebar)"
      v-if="$page.path.startsWith(item)"
    >
      <div class="group-item" v-for="temp in $site.themeConfig.sidebar[item]">
        <span class="title">{{ temp.title }}</span>
        <div class="group-list">
          <router-link
            :to="item + listitem + '.html'"
            v-for="listitem in temp.children"
            class="sidebar-link"
            active-class="active"
            >{{
              $site.pages.find(
                (page) => "/" + page.relativePath === item + listitem + ".md"
              ).title
            }}</router-link
          >
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: [],
      version: "",
    };
  },
  methods: {
    versionChange(version){
        let arr = this.$page.path.split('/')
        arr[arr.length-2] = version
        arr.pop()
        let target = arr.join('/')+'/'
        this.$router.push(target)
    }
  },
  updated() {
    if(this.$page.path.includes('versions'))
    {
        let arr = this.$page.path.split('/')
        let version = arr[arr.length-2]
        this.version = version
    }
  },
  mounted() {
    if(this.$page.path.includes('versions'))
    {
        let arr = this.$page.path.split('/')
        let version = arr[arr.length-2]
        this.version = version
    }
    // 获取有多少个版本
    Object.keys(this.$site.themeConfig.sidebar).map(path=>{
        if(path.split('/')[1]===this.$page.regularPath.split('/')[1])
        {
            let version = path.split('/')
            this.options.push({
                value:version[version.length-2],
                label:version[version.length-2]
            })
        }
    })
  },
};
</script>
<style scoped>
.group-list {
  display: flex;
  flex-direction: column;
}
.versions {
  margin-bottom: 20px;
}
.group .active {
  color: #417ff9;
  background-color: #417ff9;
}
.title {
  display: block;
  margin: 6px 0;
  color: #4e5969;
  font-size: 12px;
  font-weight: 400;
}
a.sidebar-link {
  width: 100%;
  height: 40px;
  display: block;
  line-height: 40px;
  padding-left: 1rem;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  box-sizing: border-box;
}
a.sidebar-link:hover {
  background: rgb(236, 242, 254);
  border-radius: 3px;
  transition: all 0.2s linear 0s;
}
a.sidebar-link.active {
  border-radius: 3px;
  color: white !important;
  background-color: #417ff9;
  font-weight: 700;
  border: none;
  -webkit-transition: all 0.2s linear 0s;
  transition: all 0.2s linear 0s;
}
.el-select {
    width: 100%;
}
::v-deep .el-select:hover .el-input__inner{
    background-color: rgb(237,242,254) !important;
}
</style>
