<template>
  <div class="container-fluid mt-4">
    <h2>
      <router-link to="/">Home ></router-link>
      <span> {{ breed }}</span>
    </h2>
    <div class="text-center" v-if="loading">
      <div class="spinner-border" role="status">
        <span class="sr-only">Loading...</span>
      </div>
    </div>
    <div class="row">
      <div v-for="(img, index) in dogs" :key="index" class="col-md-3 my-2">
        <div class="card border-0">
          <div class="card-img-top">
            <img :src="img" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['breed'],
  data() {
    return {
      dogs: [],
      loading: false,
    };
  },
  async mounted() {
    this.loading = true;
    try {
      const response = await fetch(
        `https://dog.ceo/api/breed/${this.breed}/images`,
      );
      const { message } = await response.json();
      this.dogs = message;
      this.loading = false;
    } catch (error) {
      this.loading = false;
    }
  },
};
</script>

<style scoped>
h2 {
  text-transform: capitalize;
  color: lightcoral;
}
h2 a {
  color: #2c3e50;
}
img {
  object-fit: cover;
  object-position: top center;
  width: 100%;
  height: 300px;
}
</style>
