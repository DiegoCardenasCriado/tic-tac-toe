<template>
  <div class="board">
    <div class="row">
      <Square :value=square[item] :turn="turn" :position="item" :winningSquare="winningSquare.includes(item)" @clickSquare="clickSquare" v-for="item in row1" :key="item" />
    </div>
    <div class="row">
      <Square :value=square[item] :turn="turn" :position="item" :winningSquare="winningSquare.includes(item)" @clickSquare="clickSquare" v-for="item in row2" :key="item" />
    </div>
    <div class="row">
      <Square :value=square[item] :turn="turn" :position="item" :winningSquare="winningSquare.includes(item)" @clickSquare="clickSquare" v-for="item in row3" :key="item" />
    </div>
  </div>
</template>

<script>
import Square from '../square/Square.vue'

export default {
  name: 'Board',
  components:{
    Square,
  },
  props:{
    square: Array,
    turn: String,
    winningSquare: Array
  },
  data() {
    return {
      row1:[0,1,2],
      row2:[3,4,5],
      row3:[6,7,8]
    }
  },
  methods: {
    clickSquare(position){
      this.$emit('clickSquare', position)
    }
  },
}
</script>
<style>
  .board{
    display: flex;
    flex-direction: column;
  }

  .row{
    display: flex;
  }
</style>
