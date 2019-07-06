<template>
<div class="box">
    <div class="nav">
        <div class="item">
            <div class="title" >热门城市 <i class="el-icon-arrow-right"></i></div>
            <ul>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>                
            </ul>
        </div>  
         <div class="item">
            <div class="title" >推荐城市 <i class="el-icon-arrow-right"></i></div>
            <ul>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>                
            </ul>
        </div> 
         <div class="item">
            <div class="title">奔向海岛 <i class="el-icon-arrow-right"></i></div>
            <ul>
                <li><span>1</span><span>上海</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>上海</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>上海</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>上海</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>上海</span><span>世界著名古都和现代化国际城市</span></li>                
            </ul>
        </div> 
         <div class="item">
            <div class="title">主题推荐 <i class="el-icon-arrow-right"></i></div>
            <ul>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>
                <li><span>1</span><span>北京</span><span>世界著名古都和现代化国际城市</span></li>                
            </ul>
        </div>       
    </div>
    <p>推荐城市</p>
    <div></div>
</div>
 

</template>

<script>
  export default {
    
  }
</script>

<style>
      .box{
               
         height: 550px;
         padding-left: 160px;
         padding-top:15px;        
      }
        .nav{                        
            position: absolute;                          
           
        }  
  
        .item>.title{           
            width:240px;
            height: 40px;
            line-height: 40px;
            font-size: 14px;
            padding-left: 20px;
            border: 1px solid #DCDCDC;    
            
        }
        .item>div>i{
            margin-left: 120px;
        }
         .item>ul{
             border: 1px solid #DCDCDC;
             background-color: #fff;
             opacity:1;
            list-style: none;         
            visibility: hidden;          
            position:absolute;
            left:260px;
            top:0;
            z-index: 2;

        }    
        .item>ul>li{           
           
            width: 340px;
            height: 40px;
        }
        .item:hover ul{         
            visibility: visible;
           
        }   
   
        .box>p{
            margin-top:180px;
        }

    </style>
