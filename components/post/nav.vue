<template>
<div class="nav">        
        <div class="item1" v-for='(item1,index) in data' :key='index' >{{item1.type}} 
                <i class="el-icon-arrow-right arrow"></i>
            <ul class="list">
                <li class="item2" v-for="(item2,index) in item1.children" :key='index'>
                    <span>{{index+1}}</span>
                    <span>{{item2.city}}</span>
                    <span>{{item2.desc}}</span>
                </li>                        
            </ul>
        </div>         
  
    <div class="city">推荐城市</div>
    <div></div>
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
    }
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
    span:nth-child(1){
        font-size: 20px;
        margin:0 10px;
    }
    span:nth-child(3){
        color: #989898;
        margin-left: 10px;
    }
    .city{
        width: 260px;
        height: 30px;
        border-bottom:1px solid #DCDCDC;
        padding-top:20px;
    }
 </style>
