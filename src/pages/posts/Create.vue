<template>
  <div class="col-md-6">
    <h2 class="mb-3">Create Post :</h2>
    <PostForm @formData="createPost" :button-loading="loading" button-text="Create Post" />
  </div>
</template>

<script>
import PostForm from "@/components/posts/Form.vue";
import { ref } from "@vue/reactivity";
import axios from "axios";
import Swal from "sweetalert2";
export default {
  components: {
    PostForm,
  },
  setup() {
    const loading = ref(false);
    function createPost(formData) {
               loading.value = true;
      axios
        .post("https://jsonplaceholder.typicode.com/posts", {
          title: formData.title,
          body: formData.body,
          userId: 1,
        })
        .then(function () {
          loading.value = false;
          Swal.fire({
            title: "با تشکر",
            text: "پست با موفقیت ایجاد شد",
            icon: "success",
            confirmButtonText: "حله",
          });
        })
        .catch(function (error) {
          console.log(error);
        });
    }

    return { createPost, loading };
  },
};
</script>

<style>
</style>