<script>
import { onMounted} from "vue";
import Barrage from "barrage-ui";
import data from "../utils/mockData";

export default {
  setup() {
    onMounted(() => {
      // 获取父级容器
      const container = document.getElementById("container");
      // 创建弹幕实例
      const barrage = new Barrage({
        container: container,
      });
      // 装填弹幕数据
      barrage.setData(data);

      // 获取 video 元素
      const video = document.getElementById("video");
      // 设置蒙版，毫秒级别，根据视频帧率进行计算，progress/(1000/fps)
      barrage.beforeRender = (ctx, progress) => {
        barrage.setMask("/mask" + (Math.floor(progress / 40) + 1) + ".png");
      };

      // 绑定播放事件
      video.addEventListener(
        "play",
        () => {
          barrage.play();
        },
        false
      );

      // 绑定暂停事件
      video.addEventListener(
        "pause",
        () => {
          barrage.pause();
        },
        false
      );

      // 切换播放进度
      video.addEventListener(
        "seeked",
        () => {
          barrage.goto(video.currentTime * 1000);
        },
        false
      );
    });
  },
};
</script>

<template>
  <div id="play">
    <div id="title">毕业设计成果展示————30秒经典影视视频</div>
    <div id="info">
      <span>
        播放数:9999
      </span>
      <span>
        弹幕数:9999
      </span>
      <span>
        2022-04-16 16:00
      </span>
    </div>
    <div id="container">
      <video
        id="video"
        controls
        controlsList="nofullscreen"
        src="../videos/result.mp4"
      ></video>
    </div>
  </div>
</template>

<style scoped>
#mask {
  display: none;
}

#container,
#video {
  width: 800px;
  height: 450px;
}

#container {
  margin: 0 auto;
  background-color: #ddd;
}
#title {
  font-size: 18px;
  text-align: left;
  font-weight: 500;
  color: #212121;
  margin-top: 24px;
  margin-bottom: 8px;
  margin-left:220px
}
#info{
  font-size: 12px;
  text-align: left;
  color: #999999;
  margin-left: 220px;
}
#info span{
  margin-right:12px;
}
#play{
  flex-grow: 1;
}
</style>
