<script setup>
 import PostItem from "@/components/PostItem.vue";

 const {posts} = defineProps(["posts"])
</script>

<template>
    <div>
        <h2 class="title">Список постів</h2>
        <PostItem v-for="post in posts" :post="post"/>
    </div>
</template>

<style scoped>
.title {
    text-align: center;
}
</style>