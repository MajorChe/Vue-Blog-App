<template>
  <div v-for="post in posts" :key="post">
    <PostListItem :post="post" />
    <span v-for="tag in post.tags" :key="tag">#{{tag}}</span>
  </div>
</template>

<script>
import PostListItem from "./PostListItem.vue";
export default {
  props: ["posts"],
  components: { PostListItem },
};
</script>

<style></style>