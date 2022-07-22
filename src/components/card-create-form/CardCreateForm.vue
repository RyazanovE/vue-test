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
          !(isButtonValid.title && isButtonValid.img && isButtonValid.cost)
        "
        @click="createItem"
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
        img: false,
        cost: false,
      },
      card: {
        img: "",
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
    createItem() {
      const nextId = this.cards?.[this.cards.length - 1]?.id + 1 || 1;
      this.card.id = nextId;
      this.$emit("create", this.card);
      this.card = {
        title: "",
        description: "",
        cost: null,
      };
      this.isButtonValid = {
        title: false,
        img: false,
        cost: false,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
@import "./CardCreateForm.scss";
</style>
