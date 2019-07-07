<template>
<el-row class="searchbox">
    <el-row type="flex" > 
     <el-col :span="24">
       <input type="text" placeholder="请输入想去的地方，例如：广州" class="search"><i class="el-icon-search icon"></i>
     </el-col>
    </el-row>
    <el-row type="flex" > 
     <el-col :span="24">
          <div class="recom-hot">推荐：
              <a href="">广州</a>
              <a href="">上海</a>
              <a href="">北京</a>
          </div>
     </el-col>
    </el-row>      
    <el-row type="flex" class="recommend" justify="space-between">
        <el-col :span="12"><div class="recom">推荐攻略</div></el-col>                      
        <el-col :span="3"><el-button type="primary"  icon="el-icon-edit" @click="handleToCreate">写游记</el-button></el-col>
    </el-row> 
 </el-row>        
</template>

<script>
export default {
    
    methods:{
        handleToCreate(){           
            this.$router.push({
                path: "/post/create",
            })
        }
    },     
}
</script>


<style>
.search{
    width: 718px;
    height: 36px;
    padding-left: 15px;
    border:2px solid #FEA410;   
}
 .icon{
  color:#FEA410;
  font-size: 22px;
  font-weight: 700;
  position: absolute;
  left:700px;
  top:10px;
}

.recommend{
    width: 720px;
    height: 40ppx;
    border-bottom:1px solid #EDEDED;
    margin-top:10px;
}
.recom{
    width: 75px;
    height: 40px;
    padding-top:20px;
    color: #FEA410;
    border-bottom:1px solid #FEA410;    
}
.recom-hot{
    font-size:12px;
}   

</style>

