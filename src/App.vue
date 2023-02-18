<template >
  <button v-on:click="addLike">+</button>
  <button v-on:click="addDislike">-</button>
  <div>
    лайк <strong>{{ likes }}</strong><br>
    дизлайк <strong>{{ dislikes }}</strong>
  </div>
</template>

<script>
export default {
  data() {
    return {
      likes: 0,
      dislikes: 0,
    }
  },
  methods: {
    addLike() {
      this.likes += 1;
    },
    addDislike() {
      this.dislikes -= 1;
    },
  },
}
</script>

<style ></style>