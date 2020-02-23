<template>
  <div class="container-fluid mt-4">
    <h2>Dog breeds</h2>
    <p>Just because we ❤️️ dogs!</p>
    <div class="text-center" v-if="loading">
      <div class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
      </div>
    </div>
    <div class="row">
      <div v-for="(breed, index) in breeds" :key="index" class="col-md-4 col-lg-3 my-2">
        <router-link :to="`/breeds/${breed}`">
          <div class="card shadow-sm border-0">
            <div class="card-body">{{ breed }}</div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      breeds: [],
      loading: false,
    };
  },
  async mounted() {
    this.loading = true;
    try {
      const response = await fetch('https://dog.ceo/api/breeds/list/all');
      const { message } = await response.json();
      this.breeds = Object.keys(message);
      this.loading = false;
    } catch (error) {
      this.loading = false;
    }
  },
};
</script>

<style scoped>
a {
  color: inherit;
  text-transform: capitalize;
  text-align: center;
}
</style>
