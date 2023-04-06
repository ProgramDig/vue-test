<script setup>
 import PostItem from "@/components/PostItem.vue";

 const {posts} = defineProps(["posts"])
 const emits = defineEmits(["delete"])
</script>

<template>
    <div v-if="posts.length > 0">
        <h2 class="title">Список постів</h2>
        <PostItem
            v-for="post in posts"
            :post="post"
            :key="post.id"
            @delete="emits('delete', post)"
        />
    </div>
    <h2 v-else class="zero__title">Постів немає!</h2>
</template>

<style scoped>
.title {
    text-align: center;
}
.zero__title {
    text-align: center;
    color: darkred;
}
</style>