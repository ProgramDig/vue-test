<script setup>
import {ref} from "vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";

const posts = ref([
    {id: 1, title: "JavaScript 1", body: "Опис поста 1"},
    {id: 2, title: "JavaScript 2", body: "Опис поста 2"},
    {id: 3, title: "JavaScript 3", body: "Опис поста 3"},
    {id: 4, title: "JavaScript 4", body: "Опис поста 4"},
]);

const createPost = (post) => {
    posts.value.push(post);
}
</script>

<template>
    <div class="app">
        <PostForm @create="createPost"/>
        <PostList :posts="posts"/>
    </div>
</template>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Calibri", sans-serif;
}

.app {
    margin: 15px;
}
</style>