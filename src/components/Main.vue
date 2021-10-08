<template>
  <div class="outer-component-wrapper">
    <h1>Zadanie rekrutacyjne Filip Kudliński</h1>
    <h3>
      Kliknij kafelek by go zaznaczyć. Po lewej stronie pomarańczowego pola
      możesz edytować tytuł zaznaczonego kafelka.
    </h3>
    <h3>
      Po prawej stronie pomarańczowego pola znajduje się przycisk służący do
      mieszania kolejności kafelków. Miłej zabawy! ;)
    </h3>
    <div class="nav">
      <input
        type="text"
        v-model="selectedTitle"
        @input="handleChange"
        :disabled="selected === 0"
      />
      <button class="shuffle" @click="shuffle()">Shuffle!</button>
    </div>
    <div class="grid-container">
      <Card
        v-for="card in shuffledCards.cards"
        :key="card.id"
        :class="{ selected: selected === card.id }"
        @click.native="select(card)"
      >
        {{ card.title }}
      </Card>
    </div>
  </div>
</template>

<script>
import Card from "@/components/Card";

class CardsContainer {
  constructor() {
    this.cards = [
      {
        id: 1,
        title: "Title 1",
      },
      {
        id: 2,
        title: "Title 2",
      },
      {
        id: 3,
        title: "Title 3",
      },
      {
        id: 4,
        title: "Title 4",
      },
      {
        id: 5,
        title: "Title 5",
      },
      {
        id: 6,
        title: "Title 6",
      },
    ];
  }

  shuffle() {
    for (let item in this.cards) {
      let randInt = Math.floor(Math.random() * 6);
      [this.cards[item], this.cards[randInt]] = [
        this.cards[randInt],
        this.cards[item],
      ];
    }
  }
}

export default {
  components: {
    Card,
  },
  data() {
    return {
      cards: new CardsContainer(),
      selected: 0,
      selectedTitle: "",
    };
  },
  computed: {
    shuffledCards() {
      return this.cards;
    },
  },
  methods: {
    shuffle() {
      this.cards.shuffle();
      this.$forceUpdate();
    },
    select(card) {
      if (this.selected === card.id) {
        this.selected = 0;
        this.selectedTitle = "";
      } else {
        this.selected = card.id;
        this.selectedTitle = card.title;
      }
    },
    handleChange() {
      const card = this.cards.cards.find((card) => card.id === this.selected);
      card.title = this.selectedTitle;
    }
  },
};
</script>

<style scoped lang="scss">
.outer-component-wrapper {
  width: 100%;

  .nav {
    display: flex;
    width: 100%;
    background-color: #F0A500;
    height: 80px;
    border-radius: 20px 20px 0 0;
    padding: 0 150px;
    margin-top: 100px;
    align-items: center;
    justify-content: space-between;

    .shuffle {
      height: 40px;
      border-radius: 20px;
      font-size: 20px;
      padding: 0 20px;
      background-color: #E8E8E8;
      color: #334756;
      font-weight: bold;
    }

    input {
      height: 40px;
      font-size: 20px;
      border-radius: 20px;
      padding-left: 20px;
      background-color: #E8E8E8;
    }
  }

  .grid-container {
    width: 100%;
    display: grid;
    grid-template-columns: 33% 33% 33%;
    grid-template-rows: auto auto;
    column-gap: 20px;
    row-gap: 40px;
    padding: 50px;
    background-color: #E8E8E8;

    .selected {
      border: 3px solid #E8E8E8;
      box-shadow: none;
      box-shadow: inset 6px 6px 10px 0 rgba(0, 0, 0, 0.2),
        inset -6px -6px 10px 0 rgba(255, 255, 255, 0.5);
    }
  }
}
</style>
