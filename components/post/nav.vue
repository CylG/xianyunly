<template>
<div class="nav">        
        <div class="item1" v-for='(item1,index) in data' :key='index' >{{item1.type}} 
                <i class="el-icon-arrow-right arrow"></i>
            <ul class="list">
                <li class="item2" v-for="(item2,index) in item1.children" :key='index'>
                    <span class="index" @click="handleTo(item2.city)"> {{index+1}} </span>
                    <span class="city" @click="handleTo(item2.city)"> {{item2.city}} </span>
                    <span class="desc" @click="handleTo(item2.city)"> {{item2.desc}} </span>
                </li>                        
            </ul>
        </div>    
    <div class="recom-city">推荐城市</div>
    <div>
        <img class="recom-pic" src="/images/pic_sea.jpeg" alt="" @click="handlePic">
    </div>
</div>
</template>

<script>
  export default {
      data(){
        return {
            data:[]
        //    type: ""  ,      // 主题类型
        //    children: []    // 城市列表 
        }
    },
    mounted(){
        this.$axios({
            url: "/posts/cities"
        }).then(res => {
             const {data} = res.data
             this.data = data;  
        })
    },
    methods:{
        handleTo(id){                     
            this.$router.push({
                path:'/post',
                query:{city:id}
            });
            this.$axios({
                url:'/posts',
                params:{city:id}
            }).then(res=>{
                const citydata = res.data;               
                this.$emit('handleToCity',citydata)
            })
        },

        handlePic(){
            this.$router.push({
                path:'/post#'
            })
        }
        
        },
    
  }
</script>

<style>
    .nav{
        width: 260px;
        height: 550px;
        padding-left: 160px;
        padding-top:15px;      
    }
    .item1{
        width:240px;
        height:40px;
        border:1px solid #DCDCDC;
        border-bottom:none;
        line-height: 40px;
        font-size: 14px;
        padding-left: 20px
     }
    .item2{
        width: 350px;
        height: 38px;
        line-height: 38px; 
            
    }
    .list{
        visibility: hidden; 
        position:absolute;
        left:420px;
        top:75px;      
        border: 1px solid #DCDCDC;
        list-style: none;
        z-index: 2;
        background-color: #fff;
        opacity:1;
    }
    .item1:hover{       
       color: #FEA410;
       background-color:aqua;
    }
    .item1:hover .list{
         visibility: visible;
    }     
    .arrow{
        margin-left:140px;
    }
    div:nth-child(4){
        border-bottom:1px solid #DCDCDC;
    }
    .index{
        font-size: 20px;      
    }
    .city{
        margin:0 5px;
    }
    .desc{
        color: #747474;
    }
    .city:hover{
        cursor:pointer; 
        text-decoration: underline ;
    }
    .desc:hover{
         cursor:pointer; 
        text-decoration: underline ;
    }
    .recom-city{
        width: 260px;
        height: 30px;
        padding-top:20px;
        margin-bottom: 10px;
        border-bottom:1px solid #DBDBDB;
        
    }
    .recom-pic{
        width: 260px;
        height: 175px;
    }
    .recom-pic:hover{
        cursor:pointer; 
    }
 </style>
