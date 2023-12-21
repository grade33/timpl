<template>
  <section class="tips section">
    <svg
      class="tips__bg"
      xmlns="http://www.w3.org/2000/svg"
      width="355"
      height="294"
      viewBox="0 0 355 294"
      fill="none"
    >
      <path
        d="M0 52.8853C0 38.3079 11.1848 26.1692 25.7136 24.9788L324.714 0.481399C341.025 -0.854978 355 12.0223 355 28.3879V266C355 281.464 342.464 294 327 294H28C12.536 294 0 281.464 0 266V52.8853Z"
        fill="white"
      />
    </svg>
    <h2 class="tips__title">Glad you enjoyed it today</h2>
    <p class="tips__desc">
      Choose the amount you wish to tip and we will transfer it directly
    </p>
    <div class="tips__field">
      <span class="tips__field-currency">€</span>
      <input
        v-model.number="tipAmount"
        type="number"
        class="tips__field-input"
        placeholder="Tip amount"
        @input="originalTipAmount = tipAmount"
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
  props: {
    isPayCommission: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      tipAmount: 5,
      originalTipAmount: 5,
    };
  },
  watch: {
    isPayCommission(newValue) {
      if (newValue) {
        this.originalTipAmount = this.tipAmount;
        this.tipAmount = +(this.tipAmount * 1.1).toFixed(1);
      } else {
        if (this.tipAmount === this.originalTipAmount) {
          this.tipAmount = +(this.tipAmount / 1.1).toFixed(1);
        } else {
          this.tipAmount = this.originalTipAmount;
        }
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.tips {
  position: relative;
  z-index: 1;
  padding-top: 44px;
  background: none;

  &__bg {
    position: absolute;
    bottom: 0;
    left: 0;
    z-index: -1;
  }

  &__title {
    margin-bottom: 13px;
    padding: 9px 15px;
    color: #fafff6;
    font-size: 21px;
    text-align: center;
    background: #8e6cea;
    border-radius: 8px;
  }

  &__desc {
    max-width: 297px;
    margin-bottom: 14px;
    font-size: 13px;
    text-align: center;
  }

  &__field {
    position: relative;
    margin-bottom: 15px;

    &-input {
      width: 100%;
      padding: 15px 40px;
      padding-right: 50px;
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
