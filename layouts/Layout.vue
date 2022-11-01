<template>
  <div class="body">
    <Header />
    <div class="content">
      <Sidebar class="sidebar" v-if="Object.keys($site.themeConfig.sidebar).find(item=>$page.path.startsWith(item))"/>
      <Content class="inner-content" />
    </div>
    <Footer />
  </div>
</template>

<script>
import Header from "../components/Header";
import Footer from "../components/Footer";
import Sidebar from "../components/Sidebar";
import prismjs from './assets/prism.js'
import prismCss from './assets/prism.css'
export default {
  components: {
    Header,
    Footer,
    Sidebar,
  },
};
</script>
<style scoped>
.body {
  display: flex;
  flex-direction: column;
  overflow: auto;
}
.content {
  margin-top: 64px;
  width: 100%;
  display: flex;
  flex: 1;
  overflow: auto;
}
.inner-content {
  padding: 50px 150px;
  padding-top: 0;
  flex: 1;
  padding-left: 410px;
  padding-right: 280px;
}
.sidebar {
  box-sizing: border-box;
  width: 280px;
  padding: 20px;
  border-right: 1px solid #e5e8ef;
  position: fixed;
  height: 100vh;
  overflow-y: overlay;
}
.sidebar:hover::-webkit-scrollbar {
  width: 6px;
}
.sidebar::-webkit-scrollbar {
  width: 0px;
  height: 3px;
}
.sidebar::-webkit-scrollbar-corner {
  background: rgb(231,233,235);
  border-radius: 8px;
}
.sidebar::-webkit-scrollbar-thumb {
  background: rgb(231,233,235);
  border-radius: 8px;
}
.sidebar::-webkit-scrollbar-thumb:hover {
  background: rgb(203, 204, 206);
}
.sidebar::-webkit-scrollbar-track {
  background: none;
  border-radius: 8px;
}


.content::-webkit-scrollbar {
  width: 6px;
  height: 3px;
}
.content::-webkit-scrollbar-corner {
  background: rgb(231,233,235);
  border-radius: 8px;
}
.content::-webkit-scrollbar-thumb {
  background: rgb(231,233,235);
  border-radius: 8px;
}
.content::-webkit-scrollbar-thumb:hover {
  background: rgb(203, 204, 206);
}
.content::-webkit-scrollbar-track {
  background: none;
  border-radius: 8px;
}
@media screen and (max-width:600px) {
  .sidebar {
    display: none;
  }
  .inner-content {
    padding-left: 0;
    padding-right: 0;
  }
}
</style>
