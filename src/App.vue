<template>
  <div class="wrapper">
    <post-form @create="createPost" :posts="posts" />
    <post-list :posts="posts" />
  </div>
</template>

<script>
import PostForm from "./components/post-form/PostForm.vue";
import PostList from "./components/post-list/PostList.vue";
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "java", body: "11" },
        { id: 2, title: "javaww", body: "44" },
        { id: 3, title: "javsa", body: "33" },
        { id: 4, title: "javssssa", body: "22" },
      ],
    };
  },
  methods: {
    createPost(post) {
      console.log(post);
      this.posts.push(post);
    },
  },
  components: { PostForm, PostList },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  padding: 24px;
}
</style>
