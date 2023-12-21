<template>
  <section class="tips section">
    <h2 class="tips__title section__title">
      <span>How much do you want to tip?</span>
    </h2>
    <div class="tips__field">
      <span class="tips__field-currency">€</span>
      <input
        v-model="tipAmount"
        type="number"
        class="tips__field-input"
        placeholder="Tip amount"
      />
      <button
        v-if="tipAmount"
        class="tips__field-clear"
        type="button"
        @click="tipAmount = ''"
      >
        ×
      </button>
    </div>
    <div class="tips__buttons">
      <button
        v-for="clueVal in [2, 5, 10]"
        :key="clueVal"
        class="tips__btn"
        :class="{ tips__btn_selected: +clueVal === +tipAmount }"
        type="button"
        @click="tipAmount = clueVal"
      >
        {{ clueVal }}€
      </button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      tipAmount: 5,
    };
  },
};
</script>

<style lang="scss" scoped>
.tips {
  &__title {
    max-width: 232px;
  }

  &__field {
    position: relative;

    &-input {
      width: 100%;
      padding: 16px;
      font-size: 20px;
      text-align: center;
      border: 2px solid #ba79fe;
      border-radius: 15px;

      &::placeholder {
        color: rgba(186, 121, 254, 75%);
      }
    }

    &-currency {
      position: absolute;
      top: 50%;
      left: 15px;
      color: #8e6cea;
      font-size: 21px;
      line-height: 1;
      transform: translateY(-50%);
    }

    &-clear {
      position: absolute;
      top: 50%;
      right: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 36px;
      height: 36px;
      font-size: 31px;
      line-height: 1;
      background-color: #eff2f9;
      border-radius: 50%;
      transform: translateY(-50%);
    }
  }

  &__buttons {
    display: flex;
    gap: 13px;
    font-size: 24px;
  }

  &__btn {
    flex-grow: 1;
    padding: 14px;
    text-align: center;
    background: rgba(186, 121, 254, 15%);
    border-radius: 20px;
    transition: background-color 0.2s ease-in-out;

    &_selected {
      background: #96ff43;
    }
  }
}
</style>
