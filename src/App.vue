<template>
  <div id="app">
    <AddPost @add-post="addPost"/>
    <div class="JSON-placeholder">
      <button name="json-placeholder" @click="this.getItem">Загрузить</button>
      <label for="json-placeholder">JSON Placeholder</label>
    </div>
    
    <PostList
      v-bind:posts="posts"
      @delete-post="deletePost"
      v-if="posts.length"
    />
    <p v-else>Постов пока нету!</p>
    <router-view />
  </div>
</template>

<script>
import PostList from "./components/PostList";
import AddPost from "./components/AddPost";
export default {
  name: "app",
  data() {
    return {
      posts: [],
      
    };
  },
  components: {
    PostList,
    AddPost,
  },
  methods: {
    getItem() {
      fetch("http://jsonplaceholder.typicode.com/posts?_limit=10")
        .then((res) => res.json())
        .then((data) => (this.posts = data));
    },
    addPost(post) {
      this.posts.push(post);
      // localStorage.setItem("posts", JSON.stringify(posts))
    },
    deletePost(id) {
      this.posts = this.posts.filter((post) => post.id !== id);
    },
   
  },
 
};
</script>
<style scope>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.JSON-placeholder {
  padding: 10px;
  border: 1px solid #000;
  border-radius: 5px;
  background-color: #7696d6;
  color: #fff;
}
</style>
