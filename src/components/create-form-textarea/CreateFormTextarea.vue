<template lang="">
  <div class="card-from__group form-group">
    <label class="form-group__label">{{ label }}</label>
    <textarea
      @input="inputHandler"
      :placeholder="placeholder"
      v-model="modelValue"
      class="form-group__input form-group__input_large"
    />
  </div>
</template>
<script>
export default {
  props: {
    label: String,
    placeholder: String,
    modelValue: [String, Number],
  },
  methods: {
    inputHandler(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
<style lang="scss" scoped>
.card-form {
  top: 16px;
  position: sticky;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 16px;

  padding: 24px;
  border-radius: 4px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04);

  &__button {
    padding: 10px;
    color: #b4b4b4;
    font-weight: 600;
    font-size: 12px;
    background: #eeeeee;
    border-radius: 10px;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    cursor: pointer;
    background-color: #7bae73;
    transition: all 0.3s ease;
    color: white;
    &:hover {
      opacity: 0.8;
    }
    &:active {
      background-color: #dbdada;
    }
    &:disabled {
      background: #eeeeee !important;
      cursor: default;
      color: #b4b4b4;
    }
  }
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 4px;

  &__label {
    font-size: 13px;
    letter-spacing: -0.02em;
    color: #49485e;

    &_dot {
      position: relative;

      &::after {
        position: absolute;
        display: inline-block;
        border-radius: 50%;
        content: "";
        color: transparent;
        height: 4px;
        width: 4px;
        background-color: #ff8484;
      }
    }
  }
  &__input {
    line-height: 15px;
    padding: 16px 12px;
    resize: none;
    border-radius: 4px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);

    &_large {
      min-height: 108px;
    }

    &::placeholder {
      font-size: 12px;
      color: #b4b4b4;
    }
  }
}
</style>
