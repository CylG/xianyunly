<template>
<el-row class="searchbox">
    <el-row type="flex" > 
     <el-col :span="24">
       <input type="text" :value="toCity" placeholder="请输入想去的地方，例如：广州" class="search"><i class="el-icon-search icon"></i>
     </el-col>
    </el-row>
    <el-row type="flex" > 
     <el-col :span="24">
          <div class="recom-hot">推荐：
              <span class="gz" @click="handleToGz">广州</span>
              <span class="sh" @click="handleToSh">上海</span>
              <span class="bj" @click="handleToBj">北京</span>          
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
    data(){
        return {
            toCity:'',
        }
    },
    
    methods:{
        handleToCreate(){           
            this.$router.push({
                path: "/post/create",
            })
        },

        handleToGz(){           
            this.toCity = '广州';
            this.$router.push({
                path:'/post',
            });
            this.$axios({
                url:'/posts',
                params:{city:'广州'}
            }).then(res=>{
                const citydata = res.data;               
                this.$emit('handleToCity',citydata)
            })
        },
              handleToSh(){           
            this.toCity = '上海';
            this.$router.push({
                path:'/post',
            });
            this.$axios({
                url:'/posts',
                params:{city:'上海'}
            }).then(res=>{
                const citydata = res.data;               
                this.$emit('handleToCity',citydata)
            })
        },
              handleToBj(){           
            this.toCity = '北京';
            this.$router.push({
                path:'/post',
            });
            this.$axios({
                url:'/posts',
                params:{city:'北京'}
            }).then(res=>{
                const citydata = res.data;               
                this.$emit('handleToCity',citydata)
            })
        },
        
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
     color: #747474;
     margin-top:10px;
} 
.gz:hover{
     cursor:pointer; 
    text-decoration: underline ;
    color: #FEA410;
}
.sh:hover{
     cursor:pointer; 
    text-decoration: underline ;
    color: #FEA410;
}
.bj:hover{
     cursor:pointer; 
    text-decoration: underline ;
    color: #FEA410;
}


</style>

