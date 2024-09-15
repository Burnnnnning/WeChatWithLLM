<template>
    <a-row style="line-height: 48px; border-bottom: solid 1px #cdcdcd;">
        <a-col :span="2" @click="message.info('点击了返回按钮')">
            <a-flex justify="center" align="center" style="font-size: 20px; height: 100%;">
                <LeftOutlined />
            </a-flex>
        </a-col>
        <a-col :span="20">
            <a-flex justify="center" style="font-size: 24px;" >聊天对象</a-flex>
        </a-col>
        <a-col :span="2" style="font-size: 24px; height: 100%;" align="center" @click="message.info('点击了聊天详情按钮')">
            <EllipsisOutlined />
        </a-col>
    </a-row>
</template>

<script setup>
import {message} from 'ant-design-vue';
import { LeftOutlined, EllipsisOutlined } from '@ant-design/icons-vue';
</script>

<style scoped></style>