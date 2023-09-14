<script setup>
import ChessBoardDisplay from "./components/ChessBoardDisplay.vue";
import SideBarComponent from "./components/SideBar.vue";
import { ref } from "vue";

const moves = ref([]); // Data property to hold moves

// Event handler for moves-updated event
function handleMovesUpdated(updatedMoves) {
  moves.value = updatedMoves;
  console.log(moves.value);
}
</script>
<template>
  <!-- <h2>hellow wo</h2> -->
  <main id="mainContainer">
    <div id="chessBoardContainer">
      <ChessBoardDisplay
        @moves-updated="handleMovesUpdated"
      />
    </div>
    <SideBarComponent id="sideBar" />
  </main>
</template>
<style>
@media (min-width: 481px) {
  #mainContainer {
    display: flex;
    /* align-items: center; */
    width: 100%;
    max-width: 100%;
    height: 98vh;
    
  }
  #chessBoardContainer {
    width: 70%;
    align-self: center;
    padding: 0;
    margin: 0;
    margin: 0 1em;
  }
  #sideBar {
    height: 100%;
    position: relative;
    right: 0%;
    top: 0%;
    background-color: black;
    width: 30%;
    /* margin-left: 1em; */
  }
}
@media screen and (min-width: 0px) and (max-width: 480px) {
  #mainContainer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    /* width: 100%;
    max-width: 100%; */
    height: 96%;
  }
  #sideBar {
    height: 40em;
    width: 100%;
    /* position: absolute; */
    /* bottom: 0%; */
    background-color: black;
    margin: 0;
  }
}
</style>
