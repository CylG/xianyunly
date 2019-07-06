<template>
    <div class="searchbox">
  
        <input type="text" placeholder="请输入想去的地方，例如：广州" class="search"><i class="el-icon-search icon"></i>
        <p>推荐：</p>

        <div class="recommend">
            <el-row type="flex" class="row-bg" justify="space-between">
             <el-col :span="6"><div class="recom">推荐攻略</div></el-col>                      
            <el-col :span="6"><el-button type="primary"  icon="el-icon-edit" @click="handleToCreate">写游记</el-button></el-col>
            </el-row>
               
               
        </div>
      
       
    </div>
</template>

<script>
export default {
    
    methods:{
        handleToCreate(){           
            this.$router.push({
                path: "/post/create",
            })
        }
    }
}
</script>


<style>
.searchbox{
    position: absolute;
    height: 140px;
}
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
.searchbox > p{
    font-size:14px;
    margin-top:10px;
}
.recommend{
    width: 720px;
    height: 40ppx;
    border-bottom:1px solid #EDEDED;
}
.recom{
    width: 75px;
    height: 40px;
    padding-top:20px;
    color: #FEA410;
    border-bottom:1px solid #FEA410;
    
    
}

   

</style>

