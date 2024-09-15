<template>
    <a-row>
        <a-col :span="20" style="padding: 5px;" :offset="2">
            <a-flex justify="flex-end">
                <div class="rightMessageCard">{{ props.message }}</div>
            </a-flex>
        </a-col>
        <a-col :span="2">
            <img src="/src/assets/b.jpg" width="100%" style="padding: 3px;" />
        </a-col>
    </a-row>
</template>

<script setup>

const props = defineProps(["message"]);

</script>

<style>
.rightMessageCard {
    width: fit-content;
    height: 100%;
    background: rgb(103 243 103);
    border-radius: 6px;
    line-height: 34px;
    font-size: 16px;
    padding-left: 8px;
    padding-right: 8px;
}
</style>
