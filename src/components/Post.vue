<template>
  <div>
    <span>
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
    </span>
    <button  >✍</button>
    <button v-on:click="$emit('delete-post', post.id)" >✘</button>
    <hr>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>
