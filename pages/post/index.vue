<template>
  <el-container>
    <el-aside width="430px">
      <Nav @handleToGz='handleToGz'/>
    </el-aside>
    <el-main>
      <Search @handleToGz='handleToGz' />
      <el-row class="recom-post" v-for='(item,index) in data' :key='index'>
        <el-row type="flex" class="post-title" >
          <el-col :span="24" >
            <div  @click="handleToDetail(item.id)">{{item.title}} </div>
             </el-col>
        </el-row>
         <el-row type="flex" class="post-content"  >
          <el-col :span="24" > 
            <div  v-html='item.summary' @click="handleToDetail(item.id)"></div>
          </el-col>
        </el-row>
        <el-row class="post-img"    >
          <el-col :span="8" v-for="(item1,index) in item.images " :key='index'>
            <img class='post-pic' :src='item1'  @click="handleToDetail(item.id)"/></el-col>    
        </el-row>
        <el-row >
          <el-col :span="4"><i class="el-icon-location-outline"></i>{{item.cityName}}</el-col>
          <el-col :span="4">by<i class="el-icon-user"></i>{{item.account.nickname}}</el-col>
          <el-col :span="4"><i class="el-icon-s-custom"></i>{{item.watch}}</el-col> 
      </el-row>        
      </el-row>   
    </el-main>
  </el-container>
</template>

<script>
import Nav from "@/components/post/nav.vue";
import Search from "@/components/post/search.vue";

export default {
    components: {
    Nav,
    Search
  },

   data(){
        return {         
            data: [],
        }   
    },

  mounted() {
    this.$axios({
      url: "/posts",
      method: "GET"
    }).then(res => {
      const {data} = res.data;
      this.data = data
    
    });
  },
  
    methods:{
      handleToDetail(itemId){        
           this.$router.push({
                // 跳转的页面路径
                path: "/post/detail",
                query: {
                    id:itemId,                 
                }
            })
          },
        
        handleToGz(gz){
          const {data} = gz
          this.data = data;
          console.log(this.data)
        }
          
        },

};
</script>

<style>
.recom-post{  
  width: 720px; 
   border-bottom:1px solid #EDEDED;
   font-size:14px;
   color: #656565;
   
      
}
.post-title{
  font-size: 18px; 
  margin:10px 0px;
  color:black;
  cursor:pointer;
}
.post-title:hover{
   color: #FEA410;
}
.post-content{
  line-height: 20px;
  height: 60px;
  overflow: hidden; 
    cursor:pointer;
}
.post-img{
 height: 154px;
  overflow:hidden;
  cursor:pointer;
}
.post-pic{
  width: 220px;
  height: 150px;
}

</style>

