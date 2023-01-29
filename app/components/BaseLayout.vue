<script setup>
  import { defineProps, defineEmits, ref } from 'vue';

  const props = defineProps({
    itemType: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  });

  //to pass data for parent component
  const emit = defineEmits(['update:itemList']);

  const itemList = ref([]);

  function fetchItems() {
    fetch(`https://jsonplaceholder.typicode.com/${props.itemType}`)
      .then(res => res.json())
      .then(res => {
        emit('update:itemList', res.splice(0, 40));
      });
  };
</script>

<template>
  <section>
    <slot name="hero" />

    <h1>{{ title }}</h1>

    <button @click="fetchItems">Fetch Item's</button>
    <slot name="controls" />

    <slot name="metrics" />

    <ul>
      <slot name="items" :itemList="itemList"/>
    </ul>
  </section>
</template>

<style></style>