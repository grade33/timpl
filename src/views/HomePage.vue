<template>
  <div class="home">
    <ProfileComp class="home__waiter" />
    <TipsComponent />
    <DottedLine />
    <RateComp />
    <DottedLine />
    <PayComp />
  </div>
</template>

<script>
import ProfileComp from '@/components/ProfileComp.vue';
import TipsComponent from '@/components/TipsComponent.vue';
import DottedLine from '@/components/UI/DottedLine.vue';
import RateComp from '@/components/RateComp.vue';
import PayComp from '@/components/PayComp.vue';

export default {
  components: { PayComp, RateComp, DottedLine, TipsComponent, ProfileComp },
};
</script>

<style lang="scss" scoped>
.home {
  max-width: 375px;
  padding: 55px 10px 30px;
  overflow: hidden;
  background: #b9b7f4;
  border-radius: 30px;

  &__waiter {
    margin-bottom: 12px;
  }
}
</style>
