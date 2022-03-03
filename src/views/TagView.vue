<template>
  <div v-if="error">
    {{ error }}
  </div>
  <div v-if="posts.length">
    <PostList :posts = "postsWithTag" />
    <TagCloud :posts="posts"/>
  </div>
</template>

<script>
import getPosts from "../composables/getPosts"
import TagCloud from "@/components/TagCloud.vue";
import PostList from '@/components/PostList.vue';
import { computed } from '@vue/runtime-core';
export default {
  components: { TagCloud, PostList },
  props: ["tag"],
  setup(props) {
    const { posts, error, load } = getPosts();
    load();
    const postsWithTag = computed(() => {
      return posts.value.filter(post => post.tags.includes(props.tag))
    })
    return { posts, error, postsWithTag };
  },
};
</script>

<style></style>
