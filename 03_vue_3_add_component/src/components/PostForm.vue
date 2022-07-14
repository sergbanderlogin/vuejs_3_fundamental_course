<template>
  <form @submit.prevent>
    <h4>Створення поста</h4>
    <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Назва">
    <input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Опис">
    <button
        class="btn"
        @click="createPost"
    >Створити
    </button>
  </form>
</template>

<script>
export default {
  name: "PostForm.vue",
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post);
      this.post = {
        title: '',
        body: '',
      }
    },
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;

}

.input {
  width: 100%;
  border: 2px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

.btn {
  margin-top: 10px;
  padding: 10px 15px;
  align-self: flex-end;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>