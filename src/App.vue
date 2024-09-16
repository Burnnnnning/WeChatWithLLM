<template>
  <div class="container" style="height: 100%;">
    <HeaderCompVue></HeaderCompVue>
    <!-- 消息展示 -->
    <div style="overflow: scroll; height: calc(100vh - 50px - 48px); scrollbar-width: none;">
      <div v-for="(item, index) in messageList" :key="index">
        <RightMessageCompVue v-if="item.position == 'right'" :message="item.message"></RightMessageCompVue>
        <LeftMessageCompVue v-if="item.position == 'left'" :message="item.message"></LeftMessageCompVue>
      </div>
    </div>
    <!-- 发送消息 -->
    <SendMessageCompVue style="position: absolute; bottom: 0px; width: 100%;" @send="handleSend"></SendMessageCompVue>
  </div>

</template>

<script setup>
import { ref } from "vue";
import HeaderCompVue from "./components/HeaderComp.vue";
import RightMessageCompVue from "./components/RightMessageComp.vue";
import LeftMessageCompVue from "./components/LeftMessageComp.vue";
import SendMessageCompVue from "./components/SendMessageComp.vue";
import axios from "axios";

const messageList = ref([]);

const handleSend = async (value) => {
  messageList.value.push({
    position: "right",
    message: value,
  });
  // 模拟回复
  // setTimeout(() => {
  //   messageList.value.push({
  //     position: 'left',
  //     message: `我收到了消息，${value}`,
  //   });
  // }, 1000);

  // 向百度云API发送请求
  const messages = messageList.value.map((item) => {
    return {
      role: item.position === "left" ? "assistant" : "user",
      content: item.message,
    };
  });

  // 记录messages
  console.log(messages);

  // axios 请求是异步的，如果需要处理返回数据，则需要转换为同步
  // GET和POST两种请求
  // GET直接通过浏览器去访问，只能传输若干个字符串参数
  // POST可以传输一个body(json格式)，对于对象的传输比较方便
  // **输入url后，才会有响应**
  const res = await axios.request({
    url: "",
    method: "POST",
    data: {
      // body的内容
      messages,
      system: "Please do not use Markdown syntax. Remember that you are a university student majoring in Computer Science and Technology.",
    },
  });
  // 记录res
  console.log(res);

  messageList.value.push({
    position: "left",
    message: res.data.result,
  });
};
</script>

<style scoped>
.container {
  width: 30%;
  height: 100%;
  left: 50%;
  position: absolute;
  background: rgb(236, 236, 236);
  transform: translateX(-50%);
}
</style>
