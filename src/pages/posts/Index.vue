<template>
  <div>
    <router-link class="btn btn-primary" :to="{ name: 'createPost' }"
      >Create Post</router-link
    >
  </div>
  <div v-if="loading" class="spinner-border text-info" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>
  <div v-else class="col-md-4" v-for="post in posts" :key="post.id">
    <div class="card">
      <div class="card-header">
        <router-link :to="{ name: 'postId', params: { id: post.id } }">
          {{ post.title }}
        </router-link>
      </div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Body : {{ post.body }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { ref } from "@vue/reactivity";
// import { useRoute } from "vue-router";

export default {
  components: {},
  setup() {
    const posts = ref([]);
    const loading = ref(true);
    // const route = useRoute();
    function getPosts() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then(function (response) {
          posts.value = response.data;
          loading.value = false;
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        });
    }
    getPosts();
    return { posts, loading };
  },
};
</script>

<style>
</style>