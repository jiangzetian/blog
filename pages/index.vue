<template>
  <div id="index">
    <div class="avatar">
      <el-avatar :src="require('@/static/image/index/avatar.jpg')" :size="160"></el-avatar>
    </div>
    <div class="text">
      <h1>天小天</h1>
      <h2>天小天一名年轻且充满活力的前端工程师！</h2>
    </div>
    <div class="contact">
      <div v-for="(item) in contactData" :key="item.id" @click="navToUrl(item.url)">
        <img :src="item.img" alt="">
      </div>
    </div>
  </div>
</template>

<script>
  import indexAPI from '@/api/modul/index';
  export default {
    components:{},
    head () {
      return {
        title:'天小天',
      }
    },
    data(){
      return{
        contactData:[],
      }
    },
    async asyncData(context){
      let contactData = await indexAPI.getContact();
      return {
        contactData,
      }
    },
    methods:{
      navToUrl(url){
        window.open(url);
      },
    },
    created() {
    },
    mounted() {
    },
  }
</script>

<style lang="scss" scoped>
  @import "@/assets/css/page/index.scss";
</style>
