<template>
  <div class="app">
    <!-- SIDEBAR -->
    <Sidebar/>
    <RouterView/>
  </div>
</template>

<script setup>
  import Sidebar from './components/Sidebar.vue';
</script>

<style lang="scss">

:root {
  --grey: #6c757d;
  --dark: #212529;
  --dark-alt: #343a40;
  --light: #dee2e6;
  --sidebar-width: 300px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
}

body {
  background: var(--light);
}

button {
  cursor: pointer;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}

.app {
  display: flex;

  main {
    flex: 1 1 0;
    padding: 2rem;

    @media (max-width: 768px) {
      padding-left: 6rem;
    }
  }
}

</style>
