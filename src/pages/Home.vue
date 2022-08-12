<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-md-6">
        <p>
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Quibusdam
          iste sed ea possimus. Corporis exercitationem enim eaque est
          necessitatibus error officiis, officia commodi inventore cumque ipsa
          nemo obcaecati consectetur eveniet.Lorem ipsum dolor sit amet
          consectetur adipisicing elit. Quibusdam iste sed ea possimus. Corporis
          exercitationem enim eaque est necessitatibus error officiis, officia
          commodi inventore cumque ipsa nemo obcaecati consectetur eveniet.
        </p>
        <router-link class="btn btn-info me-3" :to="{name:'users'}">Users</router-link>
        <router-link class="btn btn-secondary" :to="{name:'posts'}">Posts</router-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>

<style>
</style>