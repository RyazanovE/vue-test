<template>
  <div class="wrapper">
    <div class="container">
      <card-create-form @create="createItem" :cards="cards" />
      <card-list v-if="cards.length" @remove="removeItem" :cards="cards" />
      <img
        class="loader"
        src="public\images\loader.gif"
        v-else-if="isLoading"
      />
    </div>
  </div>
</template>

<script>
import CardList from "./components/card-list/CardList.vue";
import CardCreateForm from "./components/card-create-form/CardCreateForm.vue";

export default {
  data() {
    return {
      isLoading: true,
      cards: [],
    };
  },
  methods: {
    createItem(newItem) {
      this.cards.push(newItem);
    },
    removeItem(id) {
      this.cards = this.cards.filter((c) => c.id !== id);
    },
  },
  watch: {
    cards: {
      handler(newCards) {
        if (this.cards.length) {
          localStorage.setItem("tr", JSON.stringify(newCards));
        }
      },
      deep: true,
    },
  },
  created() {
    const persistCards = localStorage.getItem("tr");
    setTimeout(() => {
      if (persistCards) {
        this.cards = JSON.parse(persistCards);
      } else {
        this.cards = [
          {
            id: 1,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 2,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 3,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 4,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 5,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 6,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 7,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 8,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
          {
            id: 9,
            photo: "public\images\Rectangle 31.png",
            title: "Наименование товара",
            description:
              "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
            cost: 10000,
          },
        ];
      }
      this.isLoading = false;
    }, 1000);
  },
  components: { CardList, CardCreateForm },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600&display=swap");
@import "./reset.scss";

* {
  font-family: "Source Sans Pro", sans-serif !important;
}

.loader {
  transform: scale(0.2);
}

.wrapper {
  padding: 32px;
}

.container {
  width: 100%;
  display: flex;
  gap: 16px;

  & > * {
    flex: 1;
  }
}

@media screen and (max-width: 1200px) {
  .wrapper {
    padding: 16px;
  }
  .container {
    flex-direction: column;
  }
}
</style>
