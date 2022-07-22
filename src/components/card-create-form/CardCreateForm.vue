<template lang="">
  <card-create-form-wrapper>
    <form class="card-form" @submit.prevent>
      <create-form-input
        v-for="{ id, placeholder, label, value, isTextarea } in this.inputsArr"
        :key="id"
        :isTextarea="isTextarea"
        :placeholder="placeholder"
        :label="label"
        v-model:isDisabled="isButtonValid[value]"
        v-model="card[value]"
      />

      <button
        :disabled="
          !(isButtonValid.title && isButtonValid.photo && isButtonValid.cost)
        "
        @click="createItem(cards)"
        class="card-form__button"
        type="submit"
      >
        Добавить товар
      </button>
    </form>
  </card-create-form-wrapper>
</template>

<script>
import CreateFormInput from "../create-form-input/CreateFormInput.vue";
import CardCreateFormWrapper from "../hoc/card-create-form-wrapper/CardCreateFormWrapper.vue";
import inputsMockArr from "../../mock-data/inputs/inputs.js";
export default {
  components: { CreateFormInput, CardCreateFormWrapper },

  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      inputsArr: [],
      isButtonValid: {
        title: false,
        photo: false,
        cost: false,
      },
      card: {
        photo: "",
        title: "",
        description: "",
        cost: null,
      },
    };
  },
  created() {
    this.inputsArr = inputsMockArr;
  },
  methods: {
    createItem(cards) {
      const nextId = cards?.[cards?.length - 1]?.id + 1 || 1;
      this.card.id = nextId;
      this.$emit("create", this.card);
      console.log(this.card)
      this.card = {
        title: "",
        description: "",
        cost: null,
        photo: "",
      };
      this.isButtonValid = {
        title: false,
        photo: false,
        cost: false,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import "./CardCreateForm.scss";
</style>
