<template lang="">
  <div class="card-list-select-wrapper">
    <img class="card-list-select__arrow" src="public\images\Rectangle 33.svg" />
    <select
      @change="changeOption"
      v-model="modelValue"
      class="card-list-select"
    >
      <option disabled>По умолчанию</option>
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
      >
        {{ option.label }}
      </option>
    </select>
  </div>
</template>
<script>
export default {
  props: {
    modelValue: {
      type: String,
    },

    options: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    changeOption(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
<style scoped lang="scss">
.card-list-select-wrapper {
  position: relative;
}

.card-list-select {
  padding: 10px 27.5px 10px 16px;
  color: #b4b4b4;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  border: none;
  outline: none;
  cursor: pointer;

  -moz-appearance: none; /* Firefox */
  -webkit-appearance: none; /* Safari and Chrome */
  appearance: none;

  &__arrow {
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translate(0, -50%);
  }
}
</style>
