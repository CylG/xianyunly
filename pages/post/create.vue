<template>
    <el-container>
        <el-main>
            <p id="fabiao">发表新攻略</p>
            <p id="jianshu">分享你的个人游记，让更多人看到哦！</p>
            <el-input v-model="input" placeholder="请输入标题"></el-input>
            <div id="app">
                <VueEditor :config="config" ref="vueEditor" style="height: 400px;"/>
            </div>
            选择城市    <el-input v-model="input" placeholder="请搜索游玩城市" style="width: 200px;"></el-input><br>
            <el-button type="primary" @click="onRelease">发布</el-button>
            或者
            <el-link type="warning">保存到草稿</el-link>
        </el-main>
        <el-aside width="200px">
            <div id="drafts">
                <p id="caogao">草稿箱（0）</p>
            </div>
        </el-aside>
    </el-container>
</template>

<script>
//import VueEditor from "vue-word-editor";

// 需要单独引入样式
import "quill/dist/quill.snow.css";
let VueEditor;
if (process.browser) {
    VueEditor = require('vue-word-editor').default
}

export default {
    name: 'app',
    data() {
        return {
            input: '',
            config: {
                modules: { 
                    // 工具栏
                    toolbar: [
                        ['bold', 'italic', 'underline', 'strike'],        // toggled buttons
                        ['blockquote', 'code-block'],
                        ['image', 'video'],

                        [{ 'header': 1 }, { 'header': 2 }],               // custom button values
                        [{ 'list': 'ordered'}, { 'list': 'bullet' }],
                        [{ 'script': 'sub'}, { 'script': 'super' }],      // superscript/subscript
                        [{ 'indent': '-1'}, { 'indent': '+1' }],          // outdent/indent
                        [{ 'direction': 'rtl' }],                         // text direction
                    ]
                },
                // 主题
                theme: 'snow',
                uploadImage: {
                    url: "http://localhost:1337/upload",
                    name: "files",
                    uploadBefore(file){
                        return true
                    },
                    uploadProgress(res){

                    },
                    uploadSuccess(res, insert){
                        insert("http://localhost:1337" + res.data[0].url)
                    },
                    uploadError(){},
                    showProgress: false
                },

                uploadVideo: {
                    //url: "http://157.122.54.189:9095/upload",
                    url: "http://localhost:1337/upload",
                    name: "files",
                    uploadBefore(file){
                        return true
                    },
                    uploadProgress(res){

                    },
                    uploadSuccess(res, insert){
                        insert("http://localhost:1337" + res.data[0].url)
                    },
                    uploadError(){},
                }
            }
        }
    },
    components: {
        VueEditor
    },
    methods: {
        onRelease(){
            // 提交到添加商品的接口
            this.$axios({
                url: "/posts",
                method: "POST",
                data: this.form,
                // 处理session跨域
                withCredentials: true
            }).then(res => {
                const {status, message} = res.data;

                if(status === 0){
                    // 成功的提示
                    this.$message.success(message);
                    // 返回上一页
                    this.$router.back();
                }else{
                    // 跳转到登录页
                    this.$router.push("/login");
                }
            })
        }
    }
}
</script>

<style>
.el-container{
    width: 1000px;
    margin: 0 auto;
}

.el-aside {
    color: #333;
    text-align: center;
}
  
.el-main {
    color: #333;
}
  
body > .el-container {
    margin-bottom: 40px;
}

#fabiao{
    font-size:24px;
}

#jianshu{
    font-size: 12px;
    color:#ccc;
    padding: 10px 0px;
}

#app{
    margin:20px 0px;
    height: 450px;
}

.el-button{
    padding: 0;
    margin-top: 20px;
    height: 30px;
    width: 50px;
}

#caogao{
    float: left;
    padding-left: 10px;
}

#drafts{
    width: 190px;
    height: 50px;
    line-height: 50px;
    border: 1px solid #ccc;
    color: #666;
    margin-top: 20px;
}

</style>
