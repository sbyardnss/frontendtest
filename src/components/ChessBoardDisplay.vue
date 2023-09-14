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
  data() {
    return {
      moves: [],
    }
  },
  methods: {
    onMove(move) {
      this.moves.push(move)
      this.$emit("moves-updated", this.moves); // Emit custom event with moves
      // console.log("Move made:", move);
    },
  },
};
</script>

<style>

#chessBoardInterface {
  /* width: 100%; */
  /* height: 100vh; */
  height: 100%;
  max-width: 100%;
  
}
</style>
