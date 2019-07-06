<template>
    <el-container>
  <el-aside width="430px">
      <AsideNav />
     
  </el-aside>
  <el-main >
     <Search />
   
    
  </el-main>
</el-container>
</template>

<script>
import AsideNav from '@/components/post/asideNav.vue';
import Search from '@/components/post/search.vue';

export default {

components:{
    AsideNav,
    Search,
   
}

}
</script>

<style> 
  
  .el-aside {

    color: #333;
   
  }
  
  .el-main {
    /* background-color: #E9EEF3; */
    color: #333;
  
  }
  
  body > .el-container {
 
  }
  
 
</style>