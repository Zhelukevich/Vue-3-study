<template >
  <form @submit.prevent>
    <h2>Создание поста</h2>
    <input v-model="post.title" type="text" placeholder="Название">
    <input v-model="post.body" type="text" placeholder="Описание">
    <my-button class="btn" @click="createPost">Добавить</my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: '',
      }
    },
  }
}
</script>

<style ></style>