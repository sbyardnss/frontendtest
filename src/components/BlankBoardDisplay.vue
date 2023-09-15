<script>
export default {
  name: "BlankBoardDisplay",
  emits: ['squaresUpdated'],
  data() {
    return {
      letters: ["h", "g", "f", "e", "d", "c", "b", "a"],
      // letters: ['a','b','c','d','e','f','g','h'],
      numbers: [1, 2, 3, 4, 5, 6, 7, 8],
      // numbers: [8,7,6,5,4,3,2,1],
      blackSquares: [
        "a1",
        "a3",
        "a5",
        "a7",
        "b2",
        "b4",
        "b6",
        "b8",
        "c1",
        "c3",
        "c5",
        "c7",
        "d2",
        "d4",
        "d6",
        "d8",
        "e1",
        "e3",
        "e5",
        "e7",
        "f2",
        "f4",
        "f6",
        "f8",
        "g1",
        "g3",
        "g5",
        "g7",
        "h2",
        "h4",
        "h6",
        "h8",
      ],
      clickedSquares: [],
      activeSquare: null,
    };
  },
  methods: {
    handleSquareClicked(square) {
      this.clickedSquares.push(square);
      this.activeSquare = square;
      this.$emit("squaresUpdated", this.clickedSquares)
    },
  },
};
</script>
<template>
  <div class="column" v-for="n in this.numbers">
    <div
      v-for="l in this.letters"
      :class="{
        blackSquare: blackSquares.includes(`${l}${n}`),
        whiteSquare: !blackSquares.includes(`${l}${n}`),
        active: `${l}${n}` === activeSquare,
      }"
      @click="handleSquareClicked(`${l}${n}`)"
    >
      {{ `${l}${n}` }}
    </div>
  </div>
</template>
<style>
.blackSquare {
  background-color: black;
  font-size: 3vw;
  height: 2.5em;
  width: 2.5em;
  border: 1px solid black;
  color: black;
  cursor: pointer;
}
.whiteSquare {
  height: 2.5em;
  width: 2.5em;
  margin: 0;
  font-size: 3vw;
  border: 1px solid black;
  color: white;
  cursor: pointer;
}
.active {
  height: 2.5em;
  width: 2.5em;
  margin: 0;
  font-size: 3vw;
  border: 1px solid black;
  background-color: red;
  color: red;
  cursor: pointer;
}

@media screen and (min-width: 481px) {
  .column {
    display: flex;
    flex-wrap: wrap;
    font-size: 3vw;
  
    width: 2.5em;
    margin: 0;
    padding: 0;
  }
  
}
@media screen and (min-width: 0px) and (max-width: 480px) {
  .column {
    display: flex;
    /* width: fit-content; */
  }

  .whiteSquare {
    border: 0.01em solid black;
    height: 4em;
    width: 4em;
  }
  .blackSquare {
    border: 0.01em solid black;
    height: 4em;
    width: 4em;
  }
}
</style>
