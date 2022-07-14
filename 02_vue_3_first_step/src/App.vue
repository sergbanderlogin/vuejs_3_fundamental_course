<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Створення поста</h4>
      <input
          v-bind:value="title"
          @input="title = $event.target.value"
          class="input"
          type="text"
          placeholder="Назва">
      <input
          v-bind:value="body"
          @input="body = $event.target.value"
          class="input"
          type="text"
          placeholder="Опис">
      <button
          class="btn"
          @click="createPost"
      >Створити</button>
    </form>
    <div
        class="post"
        v-for="post in posts">
      <div><strong>Назва:</strong>{{ post.title }}</div>
      <div><strong>Опис:</strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App.vue",
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript 1', body: 'Опис поста 1'},
        {id: 2, title: 'JavaScript 2', body: 'Опис поста 2'},
        {id: 3, title: 'JavaScript 3', body: 'Опис поста 3'},
        {id: 4, title: 'JavaScript 4', body: 'Опис поста 4'},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost);
      this.title ='';
      this.body = '';
    },
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;

}

.post {
  margin-top: 15px;
  padding: 15px;
  border: 2px solid teal;
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