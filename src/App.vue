<script setup>
import ChessBoardDisplay from "./components/ChessBoardDisplay.vue"
import SideBarComponent from "./components/SideBar.vue";
import BlankBoardDisplay from "./components/BlankBoardDisplay.vue";
import { ref } from "vue";

// refs to hold moves and squares
const moves = ref([]);
const squares = ref([]);

// ref for board selection
const squaresOrMoves = ref('squares')

// Event handlers for updated events
function handleMovesUpdated(updatedMoves) {
  moves.value = updatedMoves;
}
function handleSquaresUpdated(updatedSquares) {
  squares.value = updatedSquares;
}
</script>
<template>
  <main id="mainContainer">
    <div id="buttonContainer">
      <button type="button" @click="squaresOrMoves = 'squares', moves = []">
        squares list
      </button>
      <button type="button" @click="squaresOrMoves = 'moves', squares = []">
        moves list
      </button>
    </div>
    <div id="boardsContainer">
      <div id="chessBoardContainer" v-if="squaresOrMoves === 'moves'">
        <ChessBoardDisplay @moves-updated="handleMovesUpdated" />
      </div>
      <div id="blankBoardComponent" v-if="squaresOrMoves === 'squares'">
        <BlankBoardDisplay @squaresUpdated="handleSquaresUpdated" />
      </div>
    </div>
    <SideBarComponent
      id="sideBar"
      :squaresForDisplay="squares"
      :movesForDisplay="moves"
    />
  </main>
</template>
<style>
#mainContainer {
  display: flex;
  flex-direction: column;
  padding: 0;
}
#buttonContainer {
  display: flex;
  align-self: center;
  width: fit-content;
  height: fit-content;
  margin: .5em;
}
#boardsContainer {
  margin: 0;
  padding: 0;
  width: 70%;
  display: flex;
  flex-direction: column;
}
#sideBar {
  background-color: black;
}
#blankBoardComponent {
  margin: 1em;
  align-self: center;
  width: fit-content;
}
@media (min-width: 481px) {
  #mainContainer {
    width: 100vw;
    height: 98vh;
  }

  #buttonContainer {
    align-self: flex-start;
  }
  #chessBoardContainer {
    width: 96%;
    align-self: center;
    padding: 0;
    margin: 1em;
  }
  #blankBoardComponent {
    display: flex;
    border: 1px solid black;
  }
  #sideBar {
    height: 100%;
    position: absolute;
    right: 0%;
    top: 0%;
    width: 30%;
  }
}
@media screen and (min-width: 0px) and (max-width: 480px) {
  #mainContainer {
    width: 100%;
    align-items: center;
    height: 96%;
  }
  #boardsContainer {
    width: 100%;
    align-self: center;
  }
  #chessBoardContainer {
    width: 100%;
    align-self: center;
    padding: 0;
    margin: 1em;
  }
  #blankBoardComponent {
    transform: scaleX(-1) rotate(90deg);
    border: 1px solid black;
    justify-self: center;
  }
  #sideBar {
    position: absolute;
    bottom: 0%;
    height: 16em;
    width: 100%;
    margin: 0;
  }
}
</style>
