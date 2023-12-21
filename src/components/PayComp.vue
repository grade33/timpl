<template>
  <div class="pay section">
    <div class="pay__commission">
      <div class="pay__commission-text">
        <strong class="pay__commission-title"
          >I want Philip to get the full amount</strong
        >
        <p class="pay__commission-desc">
          You compensate service commission, and $2 will be debited from your
          card.
        </p>
      </div>
      <ToggleComp
        :model-value="isPayCommission"
        @update:model-value="(e) => $emit('update:isPayCommission', e)"
      />
    </div>
    <div class="pay__buttons">
      <button
        class="pay__btn pay__btn_apple"
        :disabled="!isAgree"
        type="button"
      >
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 59 25">
          <path
            fill="#000"
            d="M10.68 3.53C10 4.33 8.9 4.98 7.8 4.89c-.13-1.1.4-2.26 1.03-2.98A4.3 4.3 0 0 1 11.7.43a4.34 4.34 0 0 1-1.01 3.1Zm1 1.57c-1.6-.09-2.95.9-3.7.9-.77 0-1.92-.85-3.18-.83A4.69 4.69 0 0 0 .82 7.6c-1.72 2.95-.45 7.3 1.2 9.7.82 1.2 1.79 2.5 3.07 2.45 1.2-.05 1.69-.79 3.15-.79 1.47 0 1.9.79 3.17.77 1.33-.03 2.16-1.19 2.97-2.38.92-1.34 1.3-2.66 1.32-2.73-.02-.02-2.55-.99-2.58-3.91-.02-2.45 2-3.61 2.1-3.68a4.52 4.52 0 0 0-3.55-1.92Zm9.16-3.3v17.8h2.77v-6.1h3.82c3.5 0 5.95-2.4 5.95-5.86a5.59 5.59 0 0 0-5.86-5.85h-6.68Zm2.77 2.32h3.18c2.4 0 3.77 1.28 3.77 3.53s-1.37 3.54-3.78 3.54H23.6V4.12Zm14.82 15.6c1.73 0 3.34-.87 4.07-2.26h.06v2.13h2.56v-8.86c0-2.57-2.06-4.22-5.22-4.22-2.94 0-5.1 1.68-5.19 3.98h2.5c.2-1.1 1.22-1.81 2.6-1.81 1.7 0 2.65.78 2.65 2.23v.99l-3.45.2c-3.21.2-4.95 1.5-4.95 3.8s1.8 3.83 4.37 3.83Zm.74-2.1c-1.48 0-2.41-.71-2.41-1.8 0-1.11.9-1.77 2.62-1.87l3.08-.2v1.01c0 1.67-1.42 2.86-3.3 2.86Zm9.36 6.81c2.7 0 3.96-1.02 5.07-4.14l4.85-13.61h-2.8l-3.26 10.51h-.06L49.08 6.68h-2.9l4.7 12.96-.26.79c-.42 1.33-1.1 1.85-2.33 1.85-.22 0-.64-.03-.81-.05v2.13c.16.05.84.07 1.05.07Z"
          />
        </svg>
      </button>
      <button class="pay__btn pay__btn_card" :disabled="!isAgree" type="button">
        Pay by card
      </button>
    </div>
    <label class="pay__agreement">
      <CheckboxComp v-model="isAgree" />
      <span class="pay__agreement-text">
        I agree with <a href="#">Terms & Conditions</a> and
        <a href="#">Privacy policy</a>
      </span>
    </label>
  </div>
</template>

<script>
import CheckboxComp from '@/components/UI/CheckboxComp.vue';
import ToggleComp from '@/components/UI/ToggleComp.vue';

export default {
  components: { ToggleComp, CheckboxComp },
  props: {
    isPayCommission: {
      type: Boolean,
      required: true,
    },
  },
  emits: ['update:isPayCommission'],
  data() {
    return {
      isAgree: false,
    };
  },
};
</script>

<style lang="scss" scoped>
.pay {
  gap: 0;

  &__commission {
    display: flex;
    gap: 10px;
    align-items: center;
    margin-bottom: 20px;

    &-title {
      font-size: 13px;
    }

    &-desc {
      color: #808191;
      font-size: 12px;
    }
  }

  &__buttons {
    display: flex;
    flex-direction: column;
    gap: 13px;
    margin-bottom: 25px;
  }

  &__btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    min-height: 60px;
    color: #3a414a;
    font-size: 18px;
    text-align: center;
    border-radius: 22px;
    transition:
      background-color 0.2s ease-in-out,
      border-color 0.2s ease-in-out;

    &:disabled {
      cursor: initial;
      opacity: 0.7;
    }

    &_apple {
      background: #fff;
      border: 1.5px solid #dde3f1;

      &:not(&:disabled) {
        &:hover,
        &:focus-visible {
          background: lighten(#dde3f1, 5%);
          border-color: lighten(#dde3f1, 5%);
        }

        &:active {
          background: #dde3f1;
          border-color: #dde3f1;
        }
      }

      svg {
        height: 24px;
      }
    }

    &_card {
      position: relative;
      z-index: 1;
      background: #96ff43;

      &::before {
        position: absolute;
        top: 50%;
        bottom: -5px;
        z-index: -1;
        width: 85%;
        height: 66%;
        background: #96ff43;
        border-radius: 22px;
        filter: blur(15px);
        transition: background-color 0.2s ease-in-out;
        content: '';
      }

      &:not(&:disabled) {
        &:hover,
        &:focus-visible {
          background: darken(#96ff43, 15%);
          border-color: darken(#96ff43, 15%);

          &::before {
            background: darken(#96ff43, 15%);
          }
        }

        &:active {
          background: darken(#96ff43, 20%);
          border-color: darken(#96ff43, 20%);

          &::before {
            background: darken(#96ff43, 20%);
          }
        }
      }
    }
  }

  &__agreement {
    display: flex;
    gap: 12px;
    margin: 0 auto;

    &-text {
      max-width: 203px;
      color: #808191;
      font-size: 12px;

      a {
        text-decoration: underline;
      }
    }
  }
}
</style>
