<template>
    <a-row>
        <a-col :span="20">
            <a-input v-model:value="inputValue" placeholder="请输入消息内容" @keyup.enter="handleSend"></a-input>
        </a-col>
        <a-col :span="4">
            <a-button type="primary" @click="handleSend" style="width: 100%">发送</a-button>
        </a-col>
    </a-row>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const emits = defineEmits(['send']);

const inputValue = ref("");

const handleSend = () => {
    emits("send", inputValue.value);
    inputValue.value = "";
};

</script>

<style></style>