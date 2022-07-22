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
@import "./CardItem.scss";
</style>
