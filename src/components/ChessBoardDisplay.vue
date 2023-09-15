<template>
  <TheChessboard id="chessBoardInterface" @move="onMove" />
</template>

<script>
import { TheChessboard } from "vue3-chessboard";
import "vue3-chessboard/style.css";
export default {
  name: "ChessBoardDisplay",
  components: {
    TheChessboard,
  },
  emits: ['moves-updated'],
  data() {
    return {
      moves: [],
    };
  },
  methods: {
    onMove(move) {
      this.moves.push(move);
      this.$emit("moves-updated", this.moves);
    },
  },
};
</script>

<style>
#chessBoardInterface {
  height: 100%;
  max-width: 100%;
}
</style>
