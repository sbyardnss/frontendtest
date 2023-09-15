<script>
export default {
  name: "SideBarComponent",
  props: {
    squaresForDisplay: {
      type: Array,
      required: true
    },
    movesForDisplay: {
      type: Array,
      required: true
    }
  },

};
</script>
<template>
  <div id="sideBarContainer">
    <div>
      <ol id="squareList" v-if="this.squaresForDisplay">
        <li class="squareListItem" v-for="square in squaresForDisplay" :key="square">{{ square }}</li>
      </ol>
      <ol id="squareList" v-if="this.movesForDisplay">
        <li class="squareListItem" v-for="move in movesForDisplay" :key="move">{{ move.piece }}{{ move.to }}</li>
      </ol>
    </div>
  </div>
</template>
<style>
#squareList {
  display: flex;
  flex-wrap: wrap;
  color: white;
}
.squareListItem {
  width: 50px;
}
</style>
