<template lang="">
  <div class="card-list">
    <div class="card-list__item card" v-for="card in cards" :key="card.id">
      <img src="public\images\Rectangle 31.png" class="card__img" />
      <ul class="card-body-wrapper card-body">
        <li class="card-body__title">{{ card.title }}</li>
        <li class="card-body__description">{{ card.description }}</li>
        <li class="card-body__cost">{{ card.cost }} руб.</li>
      </ul>
    </div>
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
};
</script>

<style scoped lang="scss">
.card-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;

  &__item {
    height: 423px;
    display: flex;
    flex-direction: column;
    gap: 16px;

    overflow: hidden;
    border-radius: 4px;
    box-shadow: 0 20px 30px rgba(0, 0, 0, 0.04);

    cursor: pointer;
  }

  .card {
    &__img {
      width: 100%;
      height: 200px;
    }
  }

  .card-body {
    display: flex;
    flex-direction: column;
    gap: 16px;
    flex: 1;

    &__title {
      font-size: 20px;
      font-weight: 600;
    }
    &__description {
      font-size: 16px;
    }
    &__cost {
      font-weight: 600;
      margin-top: auto;
      font-size: 24px;
    }
  }

  .card-body-wrapper {
    padding: 16px;
  }
}
</style>
