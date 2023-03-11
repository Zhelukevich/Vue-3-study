<template >
  <h1>Страница с постами</h1>
  <my-button style="margin: 15px 0;" @click="showDialog">
    Создать пользователя
  </my-button>
  <my-dialog v-model:show="dialogVisible">
    <PostForm @create="createPost" />
  </my-dialog>
  <PostList :posts="posts" @remove="removePost" v-if="!isPostsLoading" />
  <div v-else>
    Идет Загрузка...
  </div>
</template>

<script>
import PostForm from '@/components/PostForm.vue';
import PostList from '@/components/PostList.vue';
import axios from 'axios';

export default {
  components: {
    PostForm, PostList
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = response.data;
      } catch (error) {
        alert('Error')
      } finally {
        this.isPostsLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts()
  }
}
</script>

<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>