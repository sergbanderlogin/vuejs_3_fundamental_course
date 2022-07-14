<template>
  <div class="navbar">
    <div @click="$router.push('/')">VueJS</div>
    <div class="navbar__btns">
      <my-button @click="$router.push('/posts')">Публікації</my-button>
      <my-button style="margin-left: 20px;" @click="$router.push('/about')">Про сайт</my-button>
    </div>
  </div>
</template>

<script>
import MyButton from '@/components/UI/MyButton'

export default {
  components: {
    MyButton,
  }
}
</script>

<style scoped>
.navbar {
  height: 50px;
  background-color: lightgray;
  box-shadow: 2px 2px 4px gray;
  display: flex;
  align-items: center;
  padding: 0 15px;
}

.navbar__btns {
  margin-left: auto;
}
</style>