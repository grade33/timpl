<template>
  <div class="app">
    <HomePage />
  </div>
</template>

<script>
import HomePage from '@/views/HomePage.vue';

export default {
  components: { HomePage },
};
</script>

<style lang="scss" scoped>
.app {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
