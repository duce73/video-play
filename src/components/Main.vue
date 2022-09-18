<template>
    <div>
        <div id="header">基于Mask_RCNN与Barrage的自适应弹幕布局方法</div>
        <div id="main">
              <Video />
              <!-- <Sider /> -->
        </div>
        <div id="footer">
            <div id="thanks">
                感谢
                <a href="https://v3.cn.vuejs.org/">@Vue</a> 
                和
                <a href="https://barrage-ui.netlify.app/">@Barrage</a>
                提供的技术支持
            </div>
            <div id="author">2018116019 杜策</div>
        </div>
    </div>
</template>
<script setup>
import Video from './Video.vue';
import Sider from './Sider.vue';

</script>
<style>
#header{
    height: 54px;
    background-color: #0d4589;
    background-image: url('../assets/nwu.png');
    background-repeat: no-repeat;
    background-size: 150px auto;
    text-align: center;
    line-height: 54px;
    font-size: 24px;
    color: white;
}
#footer{
    display: flex;
    height:30px;
    background-color: #0d4589;
    color: white;
    padding-right: 20px;
    line-height: 30px;
}
#footer #thanks{
    margin-left: 20px;
}
#footer #author{
    text-align: right;
    flex-grow: 1;
}
#footer a{
    text-decoration:none;
    color: white;
}
#main{
    display: flex;
    padding: 0 20px;
    background: url('../assets/img_main_bg.jpg') no-repeat
}
</style>