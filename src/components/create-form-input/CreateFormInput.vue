<template lang="">
  <div class="card-from__group form-group">
    <label class="form-group__label form-group__label_dot">{{label}}</label>
    <input
      :placeholder="placeholder"
      :value="modelValue"
      @input="inputHandler"
      :class="applyInputStyle()"
      type="text"
    />
    <p class="form-group__alert" v-if="!isValid">Поле является обязательным</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isValid: true,
    };
  },
  props: {
    label: String,
    placeholder: String,
    isDisabled: Boolean,
    modelValue: [String, Number],
  },
  methods: {
    applyInputStyle: function () {
      return [
        this.isValid
          ? "form-group__input"
          : "form-group__input form-group__input_red",
      ];
    },
    inputHandler(e) {
      this.$emit("update:isDisabled", !!e.target.value);
      this.$emit("update:modelValue", e.target.value);
      this.isValid = !!e.target.value;
    },
  },
};
</script>

<style scoped lang="scss">
.form-group {
  display: flex;
  flex-direction: column;
  gap: 4px;

  &__alert {
    margin-top: 4px;
    font-size: 10px;
    line-height: 10px;

    letter-spacing: -0.02em;

    color: #ff8484;
  }
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
    font-size: 15px;
    padding: 16px 12px;
    resize: none;
    border-radius: 4px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border: 1px solid transparent;
    transition: all 300ms ease;

    &_red {
      border: 1px solid #ff8484;
    }
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
