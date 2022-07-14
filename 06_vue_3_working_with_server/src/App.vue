<template>
  <div class="app">
    <h1>Сторінка з постами</h1>
    <!--    <my-button @click="fetchPosts">Отримати пости</my-button>-->
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
        v-if="!isPostLoading"
    />
    <div v-else>Йде завантаження...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/MyButton";
import MyDialog from "@/components/UI/MyDialog";
import axios from "axios";

export default {
  name: "App.vue",
  components: {
    PostList,
    PostForm,
    MyButton,
    MyDialog,
  },

  data() {
    return {
      posts: [],
      dialogVisible: false,
      // modificatorValue: '',
      isPostLoading: false,
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
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        // setTimeout(async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data;
          // this.isPostLoading = false;
          // console.log(response);
        // }, 1000)
      } catch (e) {
        alert('Помилка')
      } finally {
        this.isPostLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
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

</style>