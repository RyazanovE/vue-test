<template lang="">
  <section class="card-list-container">
    <sort-select />
    <ul class="card-list">
      <card-item
        @remove="$emit('remove', card.id)"
        v-for="card in cards"
        :card="card"
        :key="card.id"
      />
    </ul>
  </section>
</template>

<script>
import SortSelect from "../sort-select/SortSelect.vue";
import CardItem from "../card-item/CardItem.vue";
export default {
  components: { CardItem, SortSelect },
  props: {
    cards: {
      type: Array,
      required: true,
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
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
</style>
