<template>
  <nav>
    <NuxtLink class="navlink" to="/">Home</NuxtLink>
    <NuxtLink class="navlink" to="/display">Display</NuxtLink>
    <NuxtLink class="navlink" to="/display/photos">Photos</NuxtLink>
    <NuxtLink class="navlink" to="/display/todos">List</NuxtLink>
  </nav>
</template>

<style scoped lang="scss">
  nav {
    position: fixed;
    top: 0px;
    left: 0px;
    width: 100vw;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 10px;
    background-color: rgb(148, 221, 221);

    .navlink {
      text-decoration: none;
      color: black;
      cursor: pointer;
      background-color: white;

      &:last-of-type {
        margin-right: 50px;
      }
    }
  }
</style>