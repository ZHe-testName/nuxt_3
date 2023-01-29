<template>
  <!-- EXERCISE CODE IS IN EXERCISE BRANCH -->
  <BaseLayout
    title="Hello Frontend Masters!!!"
    item-type="todos"
    v-model:item-list="todoList"
  >
    <template 
      v-slot:hero
    >
      <img src="../todo.jpg" alt="banner" class="banner_image"/>
    </template>

    <template v-slot:controls>
      <button
        @click="showList()"
      >Uncompleted</button>

      <button
        @click="showList(true)"
      >Completed</button>

      <hr/>
    </template>

    <template v-slot:metrics>
      <p>Completed : {{ completedList.length }} | Todo : {{ uncompletedList.length }}</p>
    </template>

    <template 
      v-slot:items
    >
      <li
        v-for="todo in (showCompleted ? completedList : uncompletedList)"
        :key="`todo-id${todo.id}`"
      >
        <input type="checkbox" :checked="todo.completed"/>
        {{todo.title}}
      </li>
    </template>
  </BaseLayout>
</template>
// Composition API
<script setup>
  //setup attr means that we will use a script section
  //with Composition API stuff
  //when we use Composition API we use vanilla JS

  import BaseLayout from './BaseLayout.vue';

  //all what we need for Vue instance are in vue module
  import { ref, computed, onMounted } from 'vue';

  // to create data-properties use ref helper func
  const todoList = ref([]);
  const showCompleted = ref(false);

  //to create computed-properties use computed helper func
  //data is in value field of returned object
  const completedList = computed(() => {
    return todoList.value.filter(todo => todo.completed)
  }); 
  const uncompletedList = computed(() => {
    return todoList.value.filter(todo => !todo.completed)
  });  

  //methods section dont need any more
  //use vanilla JS functions
  // function fetchTodoList() {
  //   fetch('https://jsonplaceholder.typicode.com/todos')
  //     .then(res => res.json())
  //     .then(res => {
  //       todoList.value = res.splice(0, 30);
  //     });
  // };

  function showList(completed) {
    if (completed) {
      showCompleted.value = true;

      return;
    };

    showCompleted.value = false;
  };

  //lifecycle hook's used like vanilla functions to
  //in setup section
  //but with on-prefix
  // onMounted(() => {
  //   fetchTodoList();
  // });
</script>

<style scoped lang="scss">
  .banner_image {
    display: block;
    margin: 0px auto;
    width: 60vw;
    height: 350px;
  }

  .heading {
    color: var(--text-color);
  }

  .list {
    color: var(--text-color);
    background-color: var(--bg-color);
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
</style>