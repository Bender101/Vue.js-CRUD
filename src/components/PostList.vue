<template>
  <div>
    <Post
      v-for="post of posts"
      v-bind:post="post"
      v-on:delete-post="deletePost"
    />
  </div>
</template>

<script>
import Post from "./Post";
export default {
  props: ["posts"],
  components: {
    Post,
  },
  methods: {
    deletePost(id) {
      this.$emit('delete-post', id)
    },
  
  }
};
</script>
