<template>
  <div v-if="loading" class="spinner-border text-info" role="status">
    <span class="visually-hidden">Loading...</span>
  </div>
  <div v-else class="col-md-6">
    <div class="card">
      <div class="card-header">
        {{ post.title }}
      </div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Body : {{ post.body }}</li>
      </ul>
      <div class="card-footer">
        <button @click="deletePost" class="btn btn-sm btn-danger me-4">
          Delete
        </button>
        <router-link
          class="btn btn-sm btn-primary me-4"
          :to="{ name: 'editPost', params: { id: post.id } }"
          >Edit</router-link
        >
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

import { useRoute } from "vue-router";
import Swal from "sweetalert2";
export default {
  components: {},
  setup() {
    const post = ref({});
    const loading = ref(true);
    const route = useRoute();
    function getPost() {
      axios
        .get(`https://jsonplaceholder.typicode.com/posts/${route.params.id}`)
        .then(function (response) {
          post.value = response.data;
          loading.value = false;
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        });
    }
    getPost();
    function deletePost() {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${route.params.id}`)
        .then(function () {
          Swal.fire({
            title: "",
            text: `پست شماره ${route.params.id} حذف شد`,
            icon: "error",
            confirmButtonText: "حله",
          });
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        });
    }
    return { post, loading, deletePost };
  },
};
</script>

<style>
</style>