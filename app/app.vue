<template>
  <!-- EXERCISE CODE IS IN EXERCISE BRANCH -->
  <main>
    <NavBar />

    <NuxtPage />
  </main>
</template>

<style lang="scss">
  @import './assets/styles/main.scss';

  * {
    box-sizing: border-box;
    margin: 0px;
    padding: 0px;
  }

  :root {
    --text-color: #{$textColor};
    --bg-color: #{$layoutBgColor};
    --header-color: #{$headerColor};
    --border-color: #{$borderColor};
  }

  main {
    padding-top: 50px;
  }
</style>
