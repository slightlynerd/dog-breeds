<template>
  <ul>
    <li v-for="user in users" v-bind:key="user.name">
      <img v-bind:src="user.photoURL" alt="picture text" />
      <p>{{ user.name }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      users: [
        {
          name: 'T Ritika Singh',
          photoURL: 'https://path-to-image.jpg',
        },
        {
          name: 'James',
          photoURL: 'https://path-to-image.jpg',
        },
        {
          name: 'Anderson',
          photoURL: 'https://path-to-image.jpg',
        },
      ],
    };
  },
};
</script>
