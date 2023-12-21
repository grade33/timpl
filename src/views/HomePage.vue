<template>
  <div class="home">
    <ProfileComp class="home__waiter" />
    <TipsComponent :is-pay-commission="isPayCommission" />
    <DottedLine />
    <RateComp />
    <DottedLine />
    <PayComp v-model:is-pay-commission="isPayCommission" />
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
  data() {
    return {
      isPayCommission: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.home {
  max-width: 355px;

  &__waiter {
    margin-bottom: 12px;
  }
}
</style>
