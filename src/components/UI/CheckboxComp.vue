<template>
  <span class="checkbox">
    <input
      :value="modelValue"
      class="checkbox__input visually-hidden"
      type="checkbox"
      name="rate-more"
      @change="$emit('update:modelValue', $event.target.checked)"
    />
    <span class="checkbox__flag">
      <svg
        class="checkbox__flag-checked"
        width="14"
        height="10"
        viewBox="0 0 14 10"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M1.58941 4.06969L5.97318 8.31288L13.2833 1.24181"
          stroke="white"
          stroke-width="2"
        />
      </svg>
    </span>
  </span>
</template>

<script>
export default {
  props: {
    modelValue: {
      type: Boolean,
      required: true,
    },
  },
  emits: ['update:modelValue'],
};
</script>

<style lang="scss" scoped>
.checkbox {
  flex: none;

  &__input {
    &:checked + .checkbox__flag {
      background: #2cef34;

      svg {
        opacity: 1;
      }
    }
  }

  &__flag {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    background: #d3dbec;
    border-radius: 8px;
    transition: background-color 0.2s ease-in-out;

    &-checked {
      opacity: 0;
      transition: opacity 0.2s ease-in-out;
    }
  }
}
</style>
