<template>
  <div class="wrapper">
    <div class="container">
      <card-create-form @create="createItem" :cards="cards" />
      <card-list v-if="cards.length" @remove="removeItem" :cards="cards" />
      <img class="loader" src="public\images\loader.gif" v-else-if="isLoading" />
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
@media screen and (max-width: 1200px) {
  .wrapper {
    padding: 16px;
  }
  .container {
    flex-direction: column;
  }
}

.loader {
  transform: scale(0.2);
}

html,
body,
description,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tdescription,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
description {
  line-height: 1;
}
input,
textarea,
button {
  font-family: inherit;
  font-size: inherit;
  outline: none;
  border: none;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
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
</style>
