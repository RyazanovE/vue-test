<template lang="">
  <section class="card-list-container">
    <sort-select :options="sortOptions" v-model="selectedSort" />
    <transition-group name="fade" tag="ul" class="card-list">
      <card-item
        @remove="$emit('remove', card.id)"
        v-for="card in cards"
        :card="card"
        :key="card.id"
      />
    </transition-group>
  </section>
</template>

<script>
import SortSelect from "../sort-select/SortSelect.vue";
import CardItem from "../card-item/CardItem.vue";
export default {
  data() {
    return {
      selectedSort: "По умолчанию",
      sortOptions: [
        { label: "По цене max", value: "cost_max" },
        { label: "По цене min", value: "cost_min" },
        { label: "По наименованию", value: "name" },
      ],
    };
  },
  components: { CardItem, SortSelect },
  props: {
    cards: {
      type: Array,
      required: true,
    },
  },
  watch: {
    selectedSort(sortType) {
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
  },
};
</script>

<style scoped lang="scss">
@media screen and (max-width: 800px) {
  .card-list {
    grid-template-columns: repeat(2, 1fr) !important;
  }
}
@media screen and (max-width: 500px) {
  .card-list {
    grid-template-columns: repeat(1, 1fr) !important;
  }
}

.card-list-container {
  display: flex;
  align-items: end;
  gap: 16px;
  flex-direction: column;
}

.card-list {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 1s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-50%);
}
</style>
