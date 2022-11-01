<template>
    <div class="header">
        <img :src="$withBase('/img/logo.png')" alt="">
        <div class="right">
            <div class="right-components">
                <div class="nav" v-for="item in $site.themeConfig.nav" >
                    <router-link v-if="item.link" :to="item.link.endsWith('/')?item.link:(item.link+'.html')" active-class="active">{{item.text}}</router-link>
                    <div class="group" v-if="item.items">
                        <span :to="item.link" class="group-name">{{item.text}}</span><span class="triangle-top"></span>
                        <div class="links">
                            <router-link :to="temp.link" v-for="temp in item.items" active-class="active">{{temp.text}}</router-link>
                        </div>
                    </div>
                </div>
            </div>
            <SearchBox/>
        </div>
    </div>
</template>
<script>
    import SearchBox from '@SearchBox'
    export default {
        components: { SearchBox }
    }
</script>
<style scoped>
    .header{
        padding: 0 24px;
        height: 64px;
        min-height: 64px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        box-shadow: 0 1px 0 0 rgb(0 0 0 / 6%), 0 4px 4px 0 rgb(0 0 0 / 2%);
        position: fixed;
        z-index: 999;
        background-color: #fff;
        width: 100%;
        box-sizing: border-box;
    }
    img {
        height: 2.3rem;
    }
    .right{
        height: 100%;
        display: flex;
        align-items: center;
    }
    .right-components {
        display: flex;
    }
    .nav {
        display: flex;
        align-items: center;
        cursor: pointer;
        margin-right: 50px;
    }
    .nav .active {
        color: #417ff9;
    }
    .group {
        position: relative;
        display: flex;
        align-items: center;
    }
    .group-name {
        padding: 10px 0;
    }
    .group:hover .links{
        display: flex;
    }
    .links {
        background-color: #fff;
        padding: .6rem 0;
        border: 1px solid;
        border-color: #ddd #ddd #ccc;
        text-align: left;
        border-radius: .25rem;
        white-space: nowrap;
        margin: 0;
        display: flex;
        flex-direction: column;
        position: absolute;
        top: 35px;
        left: -55px;
        display: none;
    }
    .links a {
        line-height: 1.7rem;
        border-bottom: none;
        font-weight: 400;
        margin-bottom: 0;
        padding: 0 1.5rem 0 1.25rem;
    }
    .triangle-top {
        margin-left: 10px;
        width: 0;
        height: 0;
        border: 6px black solid;
        border-left: 4px transparent solid;
        border-right: 4px transparent solid;
        border-bottom: 2px transparent solid;
    }
</style>