<template>
  <div class="dots">
    <span v-for="i in 18" :key="i" class="dots__item"></span>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.dots {
  position: relative;
  z-index: 2;
  display: flex;
  gap: 11px;
  align-items: center;
  width: fit-content;
  margin: 0 auto;
  margin-top: -5px;
  transform: translateY(2.5px);

  &__item {
    width: 5px;
    height: 5px;
    background: #a19bf1;
    border-radius: 50%;
  }
}
</style>
