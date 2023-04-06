<script setup>
import {ref} from "vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";

const posts = ref([
    {id: 1, title: "JavaScript 1", body: "Опис поста 1"},
    {id: 2, title: "JavaScript 2", body: "Опис поста 2"},
    {id: 3, title: "JavaScript 3", body: "Опис поста 3"},
    {id: 4, title: "JavaScript 4", body: "Опис поста 4"},
]);
const isDialogVisible = ref(false);
const createPost = (post) => {
    posts.value.push(post);
    isDialogVisible.value = false;
}
const deletePost = (post) => {
    posts.value = posts.value.filter((p) => p.id !== post.id);
}
const showDialog = () => {
    isDialogVisible.value = true;
}
</script>

<template>
    <div class="app">
        <h1 class="title__post__page">Сторінка з постами</h1>
        <MyButton @click="showDialog">
            Додати пост
        </MyButton>
        <MyDialog v-model:show="isDialogVisible" @update:show="false">
            <PostForm @create="createPost"/>
        </MyDialog>
        <PostList :posts="posts" @delete="deletePost"/>
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

.title__post__page {
    text-align: center;
}
</style>