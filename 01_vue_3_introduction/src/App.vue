<template>
  <div>Працює!</div>
  <div>
    <button @click="addLike">Like</button>
    <button @click="addDisLikes">DisLike</button>
  </div>
  <div>Кількість вподобайок <strong>{{ likes }}</strong></div>
  <div>Кількість дизлайків <strong>{{ dislikes }}</strong></div>
</template>

<script>
export default {
  name: "App.vue",
  data() {
    return {
      likes: 0,
      dislikes: 0,
    }
  },
  methods: {
    addLike() {
      this.likes += 1
    },
    addDisLikes() {
      this.dislikes += 1
    },
  }
}
</script>

<style scoped>

</style>