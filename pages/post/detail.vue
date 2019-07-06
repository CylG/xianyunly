<template>
    <el-container>
        <!-- 左侧内容 -->
        <el-main>
            <!-- 面包屑 -->
            <el-breadcrumb separator="/">
                <el-breadcrumb-item :to="{ path: '/post' }">旅游攻略</el-breadcrumb-item>
                <el-breadcrumb-item><a href="/post/detail">攻略详情</a></el-breadcrumb-item>
            </el-breadcrumb>

            <h1 id="biaoti">塞班贵？一定是你的打开方式不对！6000块玩转塞班</h1>

            <div>
                <p id="fabushijian">攻略：2019-05-22 10:57 &nbsp;&nbsp;&nbsp;&nbsp;阅读：849</p>
            </div>
            
            <p id="neirong">大家对塞班岛总存在着这样的误解，知道它是美属地盘，就理所当然地觉得这里的花费一定很高，花费高有高的玩法，那如果只有6000块的预算呢？要怎么玩？关于旅行这件事，我们要让钱花得更有道理，收下这份攻略，带你6000块花式玩转塞班。</p>
            
            <div id="tubiao">
                <div id="tb">
                    <i class="el-icon-edit-outline" id="tb1"></i>
                    <p id="tb2">评论(0)</p>
                </div>
                <div id="tb">
                    <i class="el-icon-star-off" id="tb1"></i>
                    <p style="font-size: 14px; color: #666">收藏</p>
                </div>
                <div id="tb">
                    <i class="el-icon-share" id="tb1"></i>
                    <p id="tb2">分享</p>
                </div>
                <div id="tb">
                    <i class="el-icon-thumb" id="tb1"></i>
                    <p id="tb2">点赞(0)</p>
                </div>
            </div>

            <!-- 评论 -->
            <div>
                <p id="pinglun">评论</p>
                <!-- 输入框 -->
                <el-input
                  type="textarea"
                  :rows="2"
                  placeholder="说点什么吧..."
                  v-model="textarea">
                </el-input>
                <!-- 上传 -->
                <el-upload
                  action="https://jsonplaceholder.typicode.com/posts/"
                  list-type="picture-card"
                  :on-preview="handlePictureCardPreview"
                  :on-remove="handleRemove">
                    <i class="el-icon-plus"></i>
                </el-upload>
                <el-dialog :visible.sync="dialogVisible">
                    <img width="100%" :src="dialogImageUrl" alt="">
                </el-dialog>
                <!-- 提交按钮 -->
                <el-button type="primary">提交</el-button>
                <!-- 递归组件 -->
                <div id="dg">
                    <Digui :data="list"/>
                </div>
            </div>

            <!-- 分页 -->
            <div class="block">
                <span class="demonstration"></span>
                <el-pagination
                  @size-change="handleSizeChange"
                  @current-change="handleCurrentChange"
                  :current-page="currentPage4"
                  :page-sizes="[2, 4, 6, 8]"
                  :page-size="2"
                  layout="total, sizes, prev, pager, next, jumper"
                  :total="100">
                </el-pagination>
            </div>
        </el-main>

        <!-- 右侧内容 -->
        <el-aside>
            <p id="gonglue">相关攻略</p>
            <div id="fengexian"></div>
        </el-aside>
    </el-container>
</template>

<script>
import Digui from "@/components/post/digui.vue";
export default {
    components: {
        Digui
    },
    methods: {
        handleRemove(file, fileList) {
            console.log(file, fileList);
        },
        handlePictureCardPreview(file) {
            this.dialogImageUrl = file.url;
            this.dialogVisible = true;
        },
        handleSizeChange(val) {
            console.log(`每页 ${val} 条`);
        },
        handleCurrentChange(val) {
            console.log(`当前页: ${val}`);
        }
    },
    data() {
        return {
            textarea: '',
            dialogImageUrl: '',
            dialogVisible: false,
            currentPage1: 5,
            currentPage2: 5,
            currentPage3: 5,
            currentPage4: 4,
            list: [
                {
                    type: "嘤嘤嘤",
                    children: [
                        { 
                            type: "嘤嘤嘤嘤",
                            children: [
                                { type: "嘤嘤嘤嘤嘤"},
                                { type: "" },
                            ]
                        },
                        {
                            type: "",
                            children: [
                                { type: "", }
                            ]
                        }
                    ]
                },
                {
                    type: "",
                    children: [
                        { type: ""},
                        { type: "" },
                        { type: "" }
                    ]
                }
            ]
        };
    }
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
}
.el-container{
    width: 1000px;
    margin: 0 auto;
}

.el-aside {
    width: 300px;
    color: #333;
    text-align: center;
}
  
.el-main {
    color: #333;
}
  
body > .el-container {
    margin-bottom: 40px;
}

#biaoti{
    padding: 20px 0px;
    border-bottom: 1px solid #ccc;
    font-size: 30px;
}

#fabushijian{
    float: right;
    padding: 20px 0px;
    color:#666;
}

#neirong{
    clear:both;
    line-height: 24px;
    font-size: 15px;
}

#tubiao{
     width: 350px;
     height: 100px;
     margin: 0 auto;
}

#tb{
    float: left;
    width: 50px;
    height: 50px;
    margin: 10px;
    text-align: center;
    cursor:pointer;
}

#tb1{
    font-size: 36px;
    color: orange;
}

#tb2{
    font-size: 14px;
    color: #666;
}

#gonglue{
    font-size: 18px;
    margin-top:20px;
    margin-bottom: 10px;
    float: left;
}

#fengexian{
    height: 50px;
    border-bottom: 1px solid #ccc;
}

#pinglun{
    padding-bottom: 20px;
    font-size: 20px;
}

.el-upload{
    margin-top: 10px;
    margin-bottom: 20px;
    height: 100px;
    width: 100px;
    line-height: 100px;
    float: left;
}

.el-button{
    padding: 0;
    margin-top: 10px;
    height: 30px;
    width: 60px;
    float: right;
}

#dg{
    clear: both;
    width: 655px;
    border: 1px solid #ccc;
    margin: 20px 0;
}

.block{
    text-align: center;
    clear: both;
}
</style>
