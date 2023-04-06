<script setup>
import {onMounted, ref} from "vue";
import axios from "axios";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";

const posts = ref([]);
const isDialogVisible = ref(false);
const isPostsLoading = ref(false);

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

const fetchPosts = async () => {
    try {
        isPostsLoading.value = true
        setTimeout(async () => {
            const response = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10")
            posts.value = response.data;
            isPostsLoading.value = false
        }, 1000)
    } catch (e) {
        isPostsLoading.value = false
        alert(e.message)
    }
}

onMounted(() => {
    fetchPosts()
})
</script>

<template>
    <div class="app">
        <h1 class="title__post__page">Сторінка з постами</h1>
        <MyButton
                @click="fetchPosts"
                style="margin-right: 15px"
        >
            Загрузити пости
        </MyButton>
        <MyButton
                @click="showDialog"
                style="margin-top: 15px"
        >
            Додати пост
        </MyButton>
        <MyDialog v-model:show="isDialogVisible" @update:show="false">
            <PostForm @create="createPost"/>
        </MyDialog>
        <PostList
                :posts="posts"
                @delete="deletePost"
                v-if="!isPostsLoading.value"
        />
        <div v-else class="loading">Йде завантаження постів...</div>
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

.loading {
    text-align: center;
    color: blueviolet;
}
</style>