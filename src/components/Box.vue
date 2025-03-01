<template>
    <div class="box has-text-wight-bold">
    <slot></slot>
    </div>
</template>

<script lang="js">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'BoxTask'
})
</script>

<style scoped>
.box {
    background: #faf0ca;
}
</style>