<template>
    <a-row>
        <a-col :span="2">
            <img src="/src/assets/a.jpg" width="100%" style="padding: 3px;" />
        </a-col>
        <a-col :span="20" style="padding: 5px;">
            <div class="leftMessageCard">{{ props.message }}</div>
        </a-col>
    </a-row>
</template>

<script setup>

const props = defineProps(["message"]);

</script>

<style>
.leftMessageCard {
    width: fit-content;
    height: 100%;
    background: white;
    border-radius: 6px;
    line-height: 34px;
    font-size: 16px;
    padding-left: 8px;
    padding-right: 8px;
}
</style>
