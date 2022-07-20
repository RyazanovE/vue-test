<template lang="">
  <div class="card-from__group form-group">
    <label class="form-group__label form-group__label_dot"><slot></slot></label>
    <input
      placeholder="Введите наименование товара"
      :value="modelValue"
      @input="inputHandler"
      class="form-group__input"
      type="text"
    />
  </div>
</template>
<script>
export default {
  props: {
    modelValue: [String, Number],
  },
  methods: {
    inputHandler(e) {
      this.$emit("update:modelValue", e.target.value);
    },
	
  },
};
</script>

<style scoped lang="scss">
.form-group {
  display: flex;
  flex-direction: column;
  gap: 4px;

  &__label {
    font-size: 10px;
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

    &::-webkit-input-placeholder {
      color: #b4b4b4;
      font-size: 12px;
    }
    &:-moz-placeholder {
      /* Upto Firefox 18, Deprecated in Firefox 19  */
      color: #b4b4b4;
      font-size: 12px;
    }
    &::-moz-placeholder {
      /* Firefox 19+ */
      color: #b4b4b4;
      font-size: 12px;
    }
    &:-ms-input-placeholder {
      color: #b4b4b4;
      font-size: 12px;
    }
  }
}
</style>
