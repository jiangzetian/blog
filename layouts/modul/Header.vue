<template>
    <div id="header" class="container">
        <div class="logo">
            <nuxt-link to="/" no-prefetch>天小天的个人博客</nuxt-link>
        </div>
        <div class="menu">
             <span @click="$router.push({path:'/'})">主页</span>
             <nuxt-link v-for="(item,index) in navlist" :key="item.name" :to="item.path"  no-prefetch>{{item.name}}</nuxt-link>
             <span :class="!dark?'active item':'item'" @click="closeDark">
                 <i class="el-icon-sunny"></i>
             </span>
             <span :class="dark?'active item':'item'" @click="openDark">
                 <i class="el-icon-moon"></i>
             </span>
        </div>
    </div>
</template>
<script>
export default {
    name: "Header",
    data(){
        return {
          navlist:[
            // {
            //   name:'首页',
            //   path:'/',
            //   active:false,
            // },
            {
              name:'文章',
              path:'/article',
              active:false,
            },
            {
              name:'关于',
              path:'/about',
              active:false,
            },
            {
              name:'友链',
              path:'/links',
              active:false,
            },
          ],
          dark:false,
          menuShow:false,
        }
      },
      methods:{
        navItemClick(index){
          console.log(index)
        },
        openDark(){
            this.dark = true;
            window.document.documentElement.setAttribute( "data-theme", 'dark' );
        },
        closeDark(){
            this.dark = false;
             window.document.documentElement.setAttribute( "data-theme", 'light' );
        }
    }
}
</script>
<style scoped lang="scss">
 @import "assets/css/layout/header";
</style>
