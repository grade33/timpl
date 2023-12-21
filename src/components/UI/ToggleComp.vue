<template>
  <div>
    <input
      id="switch"
      class="visually-hidden"
      :checked="modelValue"
      type="checkbox"
      @change="$emit('update:modelValue', $event.target.checked)"
    /><label for="switch">Toggle</label>
  </div>
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
label {
  position: relative;
  display: block;
  width: 54px;
  height: 30px;
  text-indent: -9999px;
  background: rgba(142, 108, 234, 40%);
  border-radius: 100px;
  cursor: pointer;
}

label::after {
  position: absolute;
  top: 3px;
  left: 3px;
  width: 24px;
  height: 24px;
  background: #fff;
  border-radius: 90px;
  transition: 0.3s;
  content: '';
}

input:checked + label {
  background: #96ff43;
}

input:checked + label::after {
  left: calc(100% - 3px);
  transform: translateX(-100%);
}

label:active::after {
  width: 35px;
}
</style>
