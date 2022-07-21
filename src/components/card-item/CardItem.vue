<template lang="">
  <li class="card-list__item card">
    <div class="card-container">
      <delete-button @click="$emit('remove', card)" />
      <img :src="card.photo ?? 'images/Rectangle 31.png'" class="card__img" />
      <ul class="card-body-wrapper card-body">
        <li class="card-body__title">{{ card.title }}</li>
        <li class="card-body__description">{{ card.description }}</li>
        <li class="card-body__cost">{{ devideThousands }} руб.</li>
      </ul>
    </div>
  </li>
</template>
<script>
import DeleteButton from "../delete-button/DeleteButton.vue";
export default {
  components: { DeleteButton },
  props: {
    card: {
      type: Object,
      required: true,
    },
  },
  computed: {
    devideThousands() {
      var parts = (this.card.cost + "").split("."),
        main = parts[0],
        len = main.length,
        output = "",
        i = len - 1;

      while (i >= 0) {
        output = main.charAt(i) + output;
        if ((len - i) % 3 === 0 && i > 0) {
          output = " " + output;
        }
        --i;
      }

      if (parts.length > 1) {
        output += "." + parts[1];
      }
      return output;
    },
  },
};
</script>

<style lang="scss">
.card-list {
  &__item {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 16px;

    border-radius: 4px;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
      0px 6px 10px rgba(0, 0, 0, 0.02);

    cursor: pointer;

    &:hover .card__delete-btn {
      opacity: 1;
    }
  }
}

.card {
  &__img {
    width: 100%;
  }
}

.card-container {
  overflow: hidden;
}
.card-body-wrapper {
  padding: 16px;
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
</style>
