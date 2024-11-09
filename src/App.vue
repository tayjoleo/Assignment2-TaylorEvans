<script setup>
  import AppHeader from './components/AppHeader.vue';
  import TodoList from './components/TodoList.vue';
</script>

<template>
  <header>
    <AppHeader />
  </header>
  <main>
    <AppHeader />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
  background-color: var(--color-secondary);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 130px;
}
.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
