<script setup>
  import {ref} from "vue";
  import MyInput from "@/components/UI/MyInput.vue";
  import MyButton from "@/components/UI/MyButton.vue";

  const post = ref({title: "", body: ""})
  const emits = defineEmits(["create"])

  const createPost = () => {
      post.value.id = Date.now();
      emits("create", post.value)
      post.value = {title: "", body: ""}
  }
</script>

<template>
    <form class="form" @submit.prevent>
        <MyInput
                v-model="post.title"
                type="text"
                placeholder="title"
        />
        <MyInput
                v-model="post.body"
                type="text"
                placeholder="body"
        />
        <MyButton
                style="margin-top: 15px"
                @click="createPost"
        >
            Додати
        </MyButton>
    </form>
</template>

<style>
.form {
    display: flex;
    flex-direction: column;
}



</style>