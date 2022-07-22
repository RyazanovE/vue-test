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
      this.$emit("sort", sortType);
    },
  },
};
</script>

<style scoped lang="scss">
@import "./CardList.scss";
</style>
