<template>
  <div>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length" class="layout">
      <div class="post-list">
        <PostList :posts="posts" />
      </div>
      <TagCloud :posts="posts" />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import getPosts from "../composables/getPosts";
import PostList from "../components/PostList.vue";
import TagCloud from "../components/TagCloud.vue";
export default {
  name: "Home",
  components: { PostList, TagCloud },
  setup() {
    const { posts, error, load } = getPosts();
    load();
    return { posts, error };
  },
};
</script>

<style>
.layout {
  display: grid;
  grid-template-columns: 3fr 1fr;
  gap: 20px;
}
</style>
