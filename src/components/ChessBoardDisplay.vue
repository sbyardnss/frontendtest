<template>
  <Chessboard />
</template>

<script>
import { Chessboard } from "vue-chessground";
import "vue-chessground/chessboard.css";
export default {
  name: "ChessBoardDisplay",
  components: {
    Chessboard,
  },
};
</script>

<style></style>
