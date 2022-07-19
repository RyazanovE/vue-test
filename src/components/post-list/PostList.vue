<template lang="">
  <div class="post-list">
    <div class="post-list__item" v-for="post in posts" v-bind:key="post.id">
      <div><strong>Name:</strong>{{ post.title }}</div>
      <div><strong>Descript:</strong>{{ post.body }}</div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.post-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.post-list__item {
  padding: 24px;
  border: 1px solid green;
}
</style>
