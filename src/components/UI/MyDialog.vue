<script setup>
const {show} = defineProps(["show"])
const emits = defineEmits(["update:show"])
const hideDialog = () => {
    emits("update:show", false)
}
</script>

<template>
    <div class="dialog" v-if="show" @click="hideDialog">
        <div @click.stop class="dialog__content">
            <slot></slot>
        </div>
    </div>
</template>

<style scoped>
.dialog {
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgb(0, 0, 0, 0.5);
    position: fixed;
    display: flex;
}

.dialog__content {
    padding: 20px;
    margin: auto;
    background: white;
    border-radius: 15px;
    min-height: 300px;
    min-width: 450px;
}
</style>