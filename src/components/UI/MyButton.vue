<script>
export default {
    name: "my-button"
}
</script>

<template>
    <button class="btn">
        <slot></slot>
    </button>
</template>

<style scoped>
.btn {
    padding: 10px 15px;
    font-weight: 700;
    background: none;
    border: 2px solid black;
    border-radius: 10px;
    align-self: flex-end;
}

.del {
    color: red;
    border-color: red;
}
</style>