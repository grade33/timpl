<template>
  <section class="rate section">
    <h2 class="rate__title section__title">Rate your experience</h2>
    <ul class="rate__stars">
      <li v-for="i in 5" :key="i" class="rate__star">
        <button class="rate__star-btn" type="button" @click="ratingValue = i">
          <svg
            class="rate__star-icon"
            :class="{ 'rate__star-icon_rated': i <= ratingValue }"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 42 40"
          >
            <path
              fill="currentColor"
              d="M18.31 2.45a3 3 0 0 1 5.38 0l3.96 8.02a3 3 0 0 0 2.26 1.64l8.85 1.29a3 3 0 0 1 1.66 5.12l-6.4 6.24a3 3 0 0 0-.87 2.66l1.52 8.81a3 3 0 0 1-4.36 3.17l-7.91-4.17a3 3 0 0 0-2.8 0l-7.9 4.17a3 3 0 0 1-4.36-3.17l1.52-8.81a3 3 0 0 0-.87-2.66l-6.4-6.24a3 3 0 0 1 1.66-5.12l8.85-1.29a3 3 0 0 0 2.26-1.64l3.96-8.02Z"
            />
          </svg>
        </button>
      </li>
    </ul>
    <div v-if="ratingValue" class="rate__feedback">
      <h3 class="rate__feedback-title">What did you enjoy the most?</h3>
      <div class="rate__form">
        <div class="rate__field-set">
          <label
            v-for="field in fieldList"
            :key="field.text"
            class="rate__field"
          >
            <CheckboxComp v-model="field.checked" />
            <span class="rate__field-text">{{ field.text }}</span>
          </label>
        </div>
        <textarea
          v-model="review"
          class="rate__textarea"
          name="review"
          placeholder="Leave comments (optional)"
          rows="2"
        ></textarea>
      </div>
    </div>
  </section>
</template>

<script>
import CheckboxComp from '@/components/UI/CheckboxComp.vue';

export default {
  components: { CheckboxComp },
  data() {
    return {
      ratingValue: 0,
      fieldList: [
        {
          text: 'Service',
          checked: false,
        },
        {
          text: 'Cleanliness',
          checked: false,
        },
        {
          text: 'Atmosphere',
          checked: false,
        },
        {
          text: 'Food quality',
          checked: false,
        },
      ],
      review: '',
    };
  },
};
</script>

<style lang="scss" scoped>
.rate {
  gap: 20px;

  &__stars {
    display: flex;
    gap: 10px;
  }

  &__star {
    &-icon {
      width: 50px;
      height: 50px;
      color: #eee9fc;
      transition: color 0.3s ease-in-out;

      &_rated {
        color: #ffd80d;
        animation: rated-star 0.75s cubic-bezier(0.215, 0.61, 0.355, 1);
      }

      @keyframes rated-star {
        0% {
          transform: scale3d(0.3, 0.3, 0.3);
          opacity: 0;
        }

        20% {
          transform: scale3d(1.1, 1.1, 1.1);
        }

        40% {
          transform: scale3d(0.9, 0.9, 0.9);
        }

        60% {
          transform: scale3d(1.03, 1.03, 1.03);
          opacity: 1;
        }

        80% {
          transform: scale3d(0.97, 0.97, 0.97);
        }

        100% {
          transform: scaleX(1);
          opacity: 1;
        }
      }
    }
  }

  &__feedback {
    display: flex;
    flex-direction: column;
    gap: 18px;
    align-items: center;

    &-title {
      color: #8e6cea;
      font-size: 13px;
    }
  }

  &__form {
    display: flex;
    flex-direction: column;
    gap: 18px;
    width: 100%;
    font-size: 14px;
  }

  &__field {
    &-set {
      display: flex;
      flex-direction: column;
      padding: 8px 16px;
      background: #eff2f9;
      border-radius: 10px;
    }

    display: flex;
    gap: 15px;
    align-items: center;

    &:not(&:last-child) {
      .rate__form-text {
        border-bottom: 1px solid #dde3f1;
      }
    }

    &-text {
      width: 100%;
      padding: 12px 0;
    }
  }

  &__textarea {
    padding: 6px 16px;
    color: #808191;
    font-weight: 500;
    font-size: 13px;
    background: #eff2f9;
    border-radius: 10px;
  }
}
</style>
