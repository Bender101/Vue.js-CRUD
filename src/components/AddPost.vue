<template>
  <form @submit.prevent="onSubmit">
    <label for="title">Заголовок*</label>
    <input type="text" name="title" v-model="title" />
    <label for="text">Текст*</label>
    <input type="text" name="text" v-model="body" />
    <button>Добавить</button>
  </form>
</template>
<script>
export default {
  props: ["post"],
  data() {
    return {
      title: "",
      body: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim() && this.body.trim()) {
        const newPost = {
          id: Date.now(),
          title: this.title,
          body: this.body,
        };
        this.$emit("add-post", newPost);
        this.title = "";
        this.body = "";
      }
    },
  },
};
</script>
<style scope>
form {
  width: 300px;
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
}
input {
  margin-bottom: 10px;
}
</style>
