<template>
        <el-container>
        <el-main>
            <el-breadcrumb separator="/">
                <el-breadcrumb-item :to="{ path: '/post' }">旅游攻略</el-breadcrumb-item>
                <el-breadcrumb-item><a href="/post/detail">攻略详情</a></el-breadcrumb-item>
            </el-breadcrumb>
            <h1 style="padding: 20px 0px; border-bottom: 1px solid #ccc; font-size: 30px;">塞班贵？一定是你的打开方式不对！6000块玩转塞班</h1>
            <div>
                <p style="float: right; padding: 20px 0px; color:#666; ">攻略：2019-05-22 10:57 &nbsp;&nbsp;&nbsp;&nbsp;阅读：849</p>
            </div>
            <p style="clear:both; line-height: 24px; font-size:15px;">大家对塞班岛总存在着这样的误解，知道它是美属地盘，就理所当然地觉得这里的花费一定很高，花费高有高的玩法，那如果只有6000块的预算呢？要怎么玩？关于旅行这件事，我们要让钱花得更有道理，收下这份攻略，带你6000块花式玩转塞班。</p>
        </el-main>
        <el-aside>
            <p style="font-size: 18px; margin-top:20px; margin-bottom: 10px; float: left;">相关攻略</p>
            <div style="height: 50px; border-bottom: 1px solid #ccc;"></div>
        </el-aside>
    </el-container>
</template>

<script>
export default {

}
</script>

<style>
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
</style>
