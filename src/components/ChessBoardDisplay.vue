<template>
  <TheChessboard @move="onMove"/>
  <div id="chessBoardContainer"></div>
</template>

<script>
import { TheChessboard } from "vue3-chessboard";
import 'vue3-chessboard/style.css';

export default {
  name: "ChessBoardDisplay",
  components: {
    TheChessboard,
  },
  methods: {
    onMove(move) {
      console.log("Move made:", move);
    },
  },
};
</script>

<style></style>
