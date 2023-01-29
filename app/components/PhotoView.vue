<template>
  <BaseLayout
    title="Photo Gallery"
    item-type="photos"
    v-model:item-list="photoGallery"
  >
    <template v-slot:metrics>
      <p>Photos in Gallery : {{ photoGallery.length }}</p>
    </template>

    <template 
      v-slot:items
    >
      <li
        class="photo_wrap"
        v-for="photo in photoGallery"
        :key="`photo-id-${photo.id}`"
      >
        <img :src="photo.thumbnailUrl" alt="user_photo"/>
      </li>
    </template>
  </BaseLayout>
</template>

<script setup>
  import BaseLayout from './BaseLayout.vue'; 
  import { ref, computed } from 'vue';

  const photoGallery = ref([]);

  const photoAmount = computed(() => {
    return photoGallery.value.length;
  });
</script>

<style scoped lang="scss">
  .header {
    color: var(--header-color);
  }

  .photo_list {
    list-style-type: none;
    display: flex;
    gap: 10px;
    flex-wrap: wrap;

    li {
      border: 4px solid var(--border-color);
    }
  }
</style>