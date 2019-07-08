<template>
  <el-container>
    <el-aside width="430px">
      <Nav @handleToCity='handleToCity'/>
    </el-aside>
    <el-main>
      <Search @handleToCity='handleToCity' />
      <el-row class="recom-post" v-for='(item,index) in dataList' :key='index'>
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
          <el-col :span="2"><i class="el-icon-location-outline"></i>{{item.cityName}}</el-col>
          <el-col :span="4">by<i class="el-icon-user"></i><span class="name">{{item.account.nickname}}</span></el-col>
          <el-col :span="17"><i class="el-icon-s-custom"></i>{{item.watch}}</el-col>
           <el-col :span="1"><span class="like">{{item.like}} 赞</span> </el-col>  
      </el-row>        
      </el-row> 
      <el-pagination
          @size-change="handleSizeChange"
          @current-change="handleCurrentChange"
          :current-page="pageIndex"
          :page-sizes="[1, 3, 6, 12]"
          :page-size="pageSize"
          layout="total, sizes, prev, pager, next, jumper"
          :total="total">
        </el-pagination>  
    </el-main>
  </el-container>
</template>

<script>
export default {
    components: {
    Nav,
    Search
  },

   data(){
        return {         
            data: [],
            
             pageIndex: 1,   // 默认显示第一页
             pageSize: 3,    // 默认显示多少条数据
             total: 0,       // 总条数
             dataList: []    // 分页之后的数据列表
        }   
    },

  mounted() {
    this.$axios({
      url: "/posts",
      method: "GET"
    }).then(res => {
      const {data} = res.data;    
      this.data = data;     
      // 总条数
      this.total = res.data.total;
      // 初始化数据
      this.pageIndex = 1;      
      // 获取第1-3条
      this.dataList = this.data.slice(0, 3);    
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
        
        handleToCity(city){
          const {data} = city
          console.log(city)
          this.data = data;           
            // 总条数
           this.total = city.total;
           // 初始化数据
           this.pageIndex = 1;      
           // 获取第1-3条
           this.dataList = this.data.slice(0, 3);   
             },
        
        // 分页切换条数触发
        handleSizeChange(value){
            this.pageSize = value;
        },
        
        // 页数切换时候触发
        handleCurrentChange(value){
            this.pageIndex = value;
            this.dataList = this.data.slice(
              (this.pageIndex - 1) * this.pageSize,(this.pageIndex*this.pageSize)
            )            
        },
     },

}
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
.name{
  color:#FEA410;
  font-size: 12px;
}
.like{
  color: #FEA410;
  font-size: 14px;
}
</style>
