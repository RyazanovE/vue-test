<template lang="">
  <div class="card-form-container">
    <h4 class="card-form-header">Добавление товара</h4>
    <form class="card-form" @submit.prevent>
      <create-form-input
        :placeholder="'Введите наименование товара'"
        v-model:isDisabled="isButtonValid.title"
        v-model="card.title"
        >Наименование товара</create-form-input
      >

      <div class="card-from__group form-group">
        <label class="form-group__label">Описание товара</label>
        <textarea
          placeholder="Введите описание товара"
          v-model="card.description"
          class="form-group__input form-group__input_large"
        />
      </div>

      <create-form-input
        :placeholder="'Введите ссылку'"
        v-model:isDisabled="isButtonValid.img"
        v-model="card.img"
        >Ссылка на изображение товара</create-form-input
      >
      <create-form-input
        :placeholder="'Введите цену'"
        v-model:isDisabled="isButtonValid.cost"
        v-model="card.cost"
        >Цена товара</create-form-input
      >

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
  </div>
</template>

<script>
import CreateFormInput from "../create-form-input/CreateFormInput.vue";
export default {
  components: { CreateFormInput },
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
    },
    validateHandler() {},
  },
};
</script>

<style lang="scss" scoped>
@media screen and (max-width: 1200px) {
  .card-form-container {
    display: none !important;
  }
  .card-form {
    position: static !important;
  }
}

.card-form-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 23%;
}

.card-form-header {
  font-size: 28px;
  font-weight: 600;
}

.card-form {
  top: 16px;
  position: sticky;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  gap: 16px;

  padding: 24px;
  margin-bottom: 24px;
  border-radius: 4px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04);

  &__button {
    padding: 10px;
    color: #b4b4b4;
    font-weight: 600;
    font-size: 12px;
    background: #eeeeee;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.3s ease;
    &:hover {
      opacity: 0.8;
    }
    &:active {
      background-color: #dbdada;
    }
    &:disabled {
      background: #eeeeee !important;
      cursor: default;
      opacity: 0.5;
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
