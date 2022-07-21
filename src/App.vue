<template>
  <div class="wrapper">
    <div class="container">
      <card-create-form @create="createItem" :cards="cards" />
      <card-list @remove="removeItem" :cards="cards" />
    </div>
  </div>
</template>

<script>
import CardList from "./components/card-list/CardList.vue";
import CardCreateForm from "./components/card-create-form/CardCreateForm.vue";

export default {
  data() {
    return {
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
    if (persistCards) {
      this.cards = JSON.parse(persistCards);
    } else {
      this.cards = [
        {
          id: 1,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 2,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 3,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 4,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 5,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 6,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 7,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 8,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
        {
          id: 9,
          photo: "url",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          cost: 10000,
        },
      ];
    }
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
