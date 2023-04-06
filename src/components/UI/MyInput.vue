<script setup>
const {modelValue} = defineProps(["modelValue"])
const emit = defineEmits(["update:modelValue"])
const updateInput = (event) => {
    emit("update:modelValue", event.target.value)
}
</script>

<template>
    <input :value="modelValue" @input="updateInput" type="text" class="input">
</template>

<style scoped>
.input {
    width: 100%;
    border: 2px solid black;
    border-radius: 15px;
    margin-top: 15px;
    padding: 10px;
}
</style>