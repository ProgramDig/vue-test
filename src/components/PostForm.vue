<script setup>
  import {ref} from "vue";
  import MyInput from "@/components/UI/MyInput.vue";
  import MyButton from "@/components/UI/MyButton.vue";

  const post = ref({title: "", body: ""})
  const emits = defineEmits(["create"])

  const createPost = () => {
      if(post.value.body === "" && post.value.title === "") {
          return alert("Заповніть всі поля в форму!")
      }
      post.value.id = Date.now();
      emits("create", post.value)
      post.value = {title: "", body: ""}
  }
</script>

<template>
    <div>
        <h2 class="form__title">Створити пост</h2>
        <form class="form" @submit.prevent>
            <MyInput
                v-model.trim="post.title"
                type="text"
                placeholder="Заголовок поста"
            />
            <MyInput
                v-model.trim="post.body"
                type="text"
                placeholder="Вміст поста"
            />
            <MyButton
                style="margin-top: 15px"
                @click="createPost"
            >
                Додати
            </MyButton>
        </form>
    </div>
</template>

<style>
.form {
    display: flex;
    flex-direction: column;
}
.form__title {
    text-align: center;
    margin-bottom: 15px;
}
</style>