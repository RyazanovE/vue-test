<template lang="">
  <div class="card-from__group form-group">
    <label :class="applyLabelStyle(isTextarea)">{{ label }}</label>
    <input
      v-if="!isTextarea"
      :placeholder="placeholder"
      :value="modelValue"
      @input="inputHandler"
      :class="applyInputStyle()"
      type="text"
    />
    <textarea
      v-else
      @input="inputHandler"
      :placeholder="placeholder"
      v-model="modelValue"
      class="form-group__input form-group__input_large"
    />
    <p class="form-group__alert" v-if="!isValid && !isTextarea">
      Поле является обязательным
    </p>
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
    isTextarea: Boolean,
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
    applyLabelStyle: function (isTextarea) {
      return [
        isTextarea
          ? "form-group__label"
          : "form-group__label form-group__label_dot",
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
@import "./CreateFormInput.scss";
</style>
