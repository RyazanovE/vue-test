<template lang="">
  <div class="card-list-select-wrapper">
    <img class="card-list-select__arrow" src="images\Rectangle 33.svg" />
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
@import "./SortSelect.scss";
</style>
