<template lang="">
  <div class="card-form-container">
    <h4 class="card-form-header">Добавление товара</h4>
    <form class="card-form" @submit.prevent>
      <div class="card-from__group form-group">
        <label class="form-group__label form-group__label_dot"
          >Наименование товара</label
        >
        <input
          placeholder="Введите наименование товара"
          v-model="card.title"
          class="form-group__input"
          type="text"
        />
      </div>
      <div class="card-from__group form-group">
        <label class="form-group__label">Описание товара</label>
        <textarea
          placeholder="Введите описание товара"
          v-model="card.title"
          class="form-group__input form-group__input_large"
        />
      </div>
      <div class="card-from__group form-group">
        <label class="form-group__label form-group__label_dot"
          >Ссылка на изображение товара</label
        >
        <input
          placeholder="Введите ссылку"
          v-model="card.title"
          class="form-group__input"
          type="text"
        />
      </div>
      <div class="card-from__group form-group">
        <label class="form-group__label form-group__label_dot"
          >Цена товара</label
        >
        <input
          placeholder="Введите цену"
          v-model="card.title"
          class="form-group__input"
          type="text"
        />
      </div>

      <button @click="createPost" class="card-form__button" type="submit">
        Добавить товар
      </button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      card: {
        title: "",
      },
    };
  },
  methods: {
    inputTitleHandler(e) {
      this.title = e.target.value;
    },
    createPost() {
      console.log(props);
      const id = 2;
      this.$emit("create", this.post);
      this.post = {
        title: "",
      };
      this.posts.push(this.post);
    },
  },
};
</script>

<style lang="scss" scoped>
.card-form-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 332px;
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
  height: 440px;
  border-radius: 4px;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04);

  &__button {
    padding: 10px;
    color: #b4b4b4;
    font-weight: 600;
    font-size: 12px;
    background: #eeeeee;
    border-radius: 10px;
  }
}

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
