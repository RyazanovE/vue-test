<template lang="">
  <form class="post-add-form" @submit.prevent>
    <h4 class="post-add-form__header">Создание поста</h4>
    <input v-model="post.title" class="post-add-form__input" type="text" />
    <button @click="createPost" class="post-add-form__button" type="submit">
      Add
    </button>
  </form>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      post: {
        title: "",
      },
    };
  },
  methods: {
    inputTitleHandler(e) {
      this.title = e.target.value;
    },
    createPost() {
      console.log(props);
      const id = 2;
      this.$emit("create", this.post);
      this.post = {
        title: "",
      };
      this.posts.push(this.post);
    },
  },
};
</script>
<style scoped>
.post-add-form {
  padding: 24px;
  border: 1px solid green;
  margin-bottom: 24px;
}

.post-add-form__button {
  min-width: 50px;
}

.post-add-form__header {
  margin-bottom: 24px;
}
</style>
