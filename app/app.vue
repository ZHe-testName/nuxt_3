<template>
  <div>
    <h1>
      Photo Gallery
    </h1>

    <br />

    <button @click="fetchPhotoGallery">Fetch Photo's</button>

    <hr/>

    <p>Number of photo's {{photoAmount}}</p>

    <ul>
      <li
        v-for="photo in photoGallery"
        :key="`photo-id-${photo.id}`"
      >
        <img :src="photo.thumbnailUrl" alt="user_photo"/>
      </li>
    </ul>
  </div>
</template>

<script>
  import { defineNuxtComponent } from '#app';

  export default defineNuxtComponent({
    data: () => ({
      photoGallery: [],
    }),
    computed: {
      photoAmount() {
        return this.photoGallery.length;
      },
    },
    methods: {
      fetchPhotoGallery() {
        fetch('https://jsonplaceholder.typicode.com/photos')
          .then(res => res.json())
          .then(res => {
            this.photoGallery = res.splice(0, 40);
          });
      },
    },
  });
</script>

<style scoped>
  ul {
    list-style-type: none;
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }
</style>