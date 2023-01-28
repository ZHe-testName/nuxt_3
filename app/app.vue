<template>
  <div>
    <h1 class="header">
      Photo Gallery
    </h1>

    <br />

    <button @click="fetchPhotoGallery">Fetch Photo's</button>

    <hr/>

    <p>Number of photo's {{photoAmount}}</p>

    <ul>
      <li
        class="photo_wrap"
        v-for="photo in photoGallery"
        :key="`photo-id-${photo.id}`"
      >
        <img :src="photo.thumbnailUrl" alt="user_photo"/>
      </li>
    </ul>
  </div>
</template>

<script setup>
  import { ref, computed } from 'vue';

  const photoGallery = ref([]);

  const photoAmount = computed(() => {
    return photoGallery.value.length;
  });

  function fetchPhotoGallery() {
    fetch('https://jsonplaceholder.typicode.com/photos')
      .then(res => res.json())
      .then(res => {
        photoGallery.value = res.splice(0, 40);
      });
  };
</script>

<style scoped lang="scss">
  @import './assets/style/main.scss';

  :root {
    --header-color: #{$headerColor};
  }

  .header {
    color: var(--header-color);
  }

  ul {
    list-style-type: none;
    display: flex;
    gap: 10px;
    flex-wrap: wrap;

    li {
      border: 4px solid #{$borderColor};
    }
  }
</style>