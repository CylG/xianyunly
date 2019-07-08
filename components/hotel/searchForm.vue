<template>
    <div class="container">
      <div class="seachFrom">
          <el-row type="flex"  align="middle">
                <el-autocomplete
                style="width:202px;margin-left:8px"
                :fetch-suggestions="queryDepartSearch"
                placeholder="请搜索出发城市"
                @select="handleDepartSelect"
                class="el-autocomplete"
                v-model="dataList.real_city"
                ></el-autocomplete>

        <!-- 时间选择器 -->
        <!-- range-separator:选择范围时的分隔符 -->
        <!-- start-placeholder：范围选择市开始日期的占位符 -->
        <!-- end-placeholder：范围选择市结束日期的占位符 -->
            <el-date-picker
          v-model="value1"
          type="daterange"
          range-separator="-"
          start-placeholder="入住日期"
          end-placeholder="离店日期">
        </el-date-picker>

        <el-input v-model="input" placeholder="人数未定" style="width:202px;margin-left:8px">
          <!-- <i class="iconfont iconuser el-input__icon"
              slot="suffix"
              @click="handleIconClick">
          </i> -->
        </el-input>

        <el-button type="primary" style="margin-left:30px">查看价格</el-button>
      </el-row>

        <!-- 文字区域 -->
        <el-row type="flex" align="middle" justify="space-between"
        >
          <div class="left_content">
            <p>区域:<a href="#" >
              全部
            </a>
            </p>
            <p>
            攻略:<a href="#">全部123465841231654321</a>
            </p>
            <p>
            均价:<a href="#">全部123465841231654321</a>
            </p>
          </div>

          <!-- 右边地图 -->
          <div style="margin:50px">
            <div id="container"></div>
          </div>
        </el-row>
      </div>
    </div>
</template>

<script>
export default {
    data() {
    return {
      pickerOptions: {
          shortcuts: [{
            // 选中后的回调函数
           onClick(){

           }
          }]
        },
        value1: '',
        value2: '',
        real_city:"",
        input:"",
        dataList:[]
      }
    },
      mounted(){
          window.onLoad  = function(){
                var map = new AMap.Map('container', {
                    zoom:11,//级别
                    center: [118.8718107, 31.32846821],//中心点坐标
                    viewMode:'3D'//使用3D视图
                });
        }
            var url = 'https://webapi.amap.com/maps?v=1.4.15&key=c02cc996ece905c0d9a1b4b539a6a684&callback=onLoad';
            var jsapi = document.createElement('script');
            jsapi.charset = 'utf-8';
            jsapi.src = url;
            document.head.appendChild(jsapi);


            this.$axios({
              url:`/hotels`,
              method:"GET"
            }).then(res=>{
              const {data} = res.data;
              // console.log(this.scenic);
              this.dataList = data;
              console.log(this.dataList[0]);
              console.log(this.dataList[0].scenic[0].name);
            })
    },
    methods:{
      queryDepartSearch(value , cb){
        console.log(value);
        if(!value){return};
        this.$axios({
          url:`/hotels`,
          method:"GET"
        }).then(res=>{
          console.log(res.data); 
        })
      },
      handleDepartSelect(item){
        console.log(item);
      }
    }
}
</script>

<style scoped lang="less">
    .container{
        width:1000px;
        margin:20px auto;
        .searchFrom{
          margin-right: 6px;
        }
        .left_content >a{
            
        }
        #container{
          width:420px;
          height:260px;
      }
    }
</style>
