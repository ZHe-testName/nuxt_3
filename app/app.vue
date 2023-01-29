<template>
  <!-- EXERCISE CODE IS IN EXERCISE BRANCH -->
  <main>
    <PhotoViewVue/>
    <ListView>
      <!-- slotProps value can't be changed -->
      <!-- <template v-slot:banner="slotProps">
        <img src="../todo.jpg" alt="banner" class="banner_image"/>
        <strong>
          Completed tasks amount : {{ slotProps.completed.length }}
        </strong>
      </template> -->
    </ListView>
  </main>
</template>
// Composition API
<script setup>
  import ListView from './components/ListView.vue';
  import PhotoViewVue from './components/PhotoView.vue';
</script>

<style lang="scss">
  @import './assets/styles/main.scss';

  :root {
    --text-color: #{$textColor};
    --bg-color: #{$layoutBgColor};
    --header-color: #{$headerColor};
    --border-color: #{$borderColor};
  }

  main {
    display: grid;
    grid-template-columns: repeat(2, 50%);
  }
</style>
