<script setup>
  import MyButton from "@/components/UI/MyButton.vue";

  const {post} = defineProps(["post"])
  const emits = defineEmits(["delete"])
</script>

<template>
    <div class="post">
        <div>
            <div><strong>Назва:</strong> {{ post.title }}</div>
            <div><strong>Опис:</strong> {{ post.body }}</div>
        </div>
        <div class="post__btn">
            <MyButton
                @click="emits('delete', post)"
            >
                Видалити
            </MyButton>
        </div>
    </div>
</template>

<style>
.post {
    margin-top: 15px;
    padding: 15px;
    border: 2px solid black;
    border-radius: 15px;

    display: flex;
    align-items: center;
    justify-content: space-between;
}
.post__btn {

}

</style>