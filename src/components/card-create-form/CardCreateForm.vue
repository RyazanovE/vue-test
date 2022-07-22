<template lang="">
  <card-create-form-wrapper>
    <form class="card-form" @submit.prevent>
      <create-form-input
        :placeholder="'Введите наименование товара'"
        :label="'Наименование товара'"
        v-model:isDisabled="isButtonValid.title"
        v-model="card.title"
      />
      


      <create-form-textarea
        :label="'Описание товара'"
        :placeholder="'Введите описание товара'"
        v-model="card.description"
      />

      <create-form-input
        :label="'Ссылка на изображение товара'"
        :placeholder="'Введите ссылку'"
        v-model:isDisabled="isButtonValid.img"
        v-model="card.img"
      />
    
      <create-form-input
        :label="'Цена товара'"
        :placeholder="'Введите цену'"
        v-model:isDisabled="isButtonValid.cost"
        v-model="card.cost"
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
import CreateFormTextarea from "../create-form-textarea/CreateFormTextarea.vue";
export default {
  components: { CreateFormInput, CardCreateFormWrapper, CreateFormTextarea },

  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
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

@media screen and (max-width: 1200px) {
  .card-form-container {
    display: none !important;
  }
  .card-form {
    position: static !important;
  }
}
</style>
