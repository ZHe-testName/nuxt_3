<template>
  <div>
    <img src="./todo.jpg" alt="banner" class="banner_image"/>
    <h1>Hello Frontend Masters!!!</h1>

    <br/>

    <button
      @click="fetchTodoList"
    >Fetch Todo's</button>

    <hr/>

    <ul>
      <li
        v-for="todo in todoList"
        :key="`todo-id${todo.id}`"
      >
        <input type="checkbox" :checked="todo.completed"/>
        {{todo.title}}
      </li>
    </ul>
  </div>
</template>

<script>
  import { defineNuxtComponent } from '#app'; //it's needs for Nuxt optimization

  export default defineNuxtComponent({
    data: () => ({
      todoList: [],
    }),
    methods: {
      fetchTodoList() {
        fetch('https://jsonplaceholder.typicode.com/todos')
          .then(res => res.json())
          .then(res => {
            this.todoList = res;
          });
      },
    },
  });
</script>

<style scoped>
 .banner_image {
    display: block;
    margin: 0px auto;
    width: 90vw;
    height: 500px;
 }
</style>
