<template>
  <app-wrapper>
    <card-create-form @create="createItem" :cards="cards" />
    <card-list
      @sort="sortCards"
      v-show="!cardsIsLoading"
      @remove="removeItem"
      :cards="cards"
    />
    <img class="loader" src="images\loader.gif"  v-show="cardsIsLoading" />
  </app-wrapper>
</template>

<script>
import CardList from "./components/card-list/CardList.vue";
import CardCreateForm from "./components/card-create-form/CardCreateForm.vue";
import AppWrapper from "./components/hoc/app-wrapper/AppWrapper.vue";
import cardsMockData from "./mock-data/cards/cards.js";

export default {
  data() {
    return {
      cardsIsLoading: true,
      cards: [],
    };
  },
  methods: {
    sortCards(sortType) {
      this.cards = [...this.cards].sort((c1, c2) => {
        switch (sortType) {
          case "cost_max":
            return c2.cost - c1.cost;
          case "cost_min":
            return c1.cost - c2.cost;
          case "name":
            return c1.title.localeCompare(c2.title);
        }
      });
    },
    createItem(newItem) {
      this.cards.push(newItem);
    },
    removeItem(id) {
      this.cards = [...this.cards].filter((c) => c.id !== id);
    },

    initializeCards() {
      const persistCards = localStorage.getItem("cards");
      setTimeout(() => {
        if (persistCards) {
          this.cards = JSON.parse(persistCards);
        } else {
          this.cards = cardsMockData;
        }
        this.cardsIsLoading = false;
      }, 1000);
    },
  },
  watch: {
    cards: {
      handler(newCards) {
        localStorage.setItem("cards", JSON.stringify(newCards));
      },
      deep: true,
    },
  },
  mounted() {
    this.initializeCards();
  },
  components: { CardList, CardCreateForm, AppWrapper },
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
  flex-basis: 77%;
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
