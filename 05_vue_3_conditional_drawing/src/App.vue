<template>
  <div class="app">
    <h1>Сторінка з постами</h1>
<!--    <input type="text" v-model="modificatorValue">-->
    <my-button @click="showDialog" style="margin: 15px 0;">
      Створити користувача
    </my-button>
    <my-dialog v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </my-dialog>
    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
  name: "App.vue",
  components: {
    PostList,
    PostForm,
  },

  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript 1', body: 'Опис поста 1'},
        {id: 2, title: 'JavaScript 2', body: 'Опис поста 2'},
        {id: 3, title: 'JavaScript 3', body: 'Опис поста 3'},
        {id: 4, title: 'JavaScript 4', body: 'Опис поста 4'},
      ],
      dialogVisible: false,
      // modificatorValue: '',
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
  },
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

</style>