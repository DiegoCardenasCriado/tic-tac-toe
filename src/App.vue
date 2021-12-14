<template>
<div class="app">
  <div class="winnerBox">
    <div v-if="turn !==null">
      Shift of <strong>{{turn}}</strong>
    </div>
    <div v-else>
      {{winner}}
    </div>
  </div>
  <Board :square="square" :winningSquare="winningSquare" :turn="turn" @clickSquare="clickSquare"/>
  <ScoreBoard :scoreX="score.X" :scoreO="score.O" />
</div>
</template>

<script>
import Board from './components/board/Board.vue'
import ScoreBoard from './components/scoreBoard/ScoreBoard.vue'
export default {
  name: 'App',
  components: {
    Board,
    ScoreBoard
    
  },
  data() {
    const turn = "X";
    const square = Array(9).fill(null);
    const score = {X:0,O:0};
    const winningPositions = [
      [0,1,2],
      [3,4,5],
      [6,7,8],
      [0,3,6],
      [1,4,7],
      [2,5,8],
      [0,4,8],
      [2,4,6],            
    ];
    const winningSquare = []
    return {
      turn,
      square,
      score,
      winningPositions,
      winningSquare,
      winner: ''
    }
  },
  methods: {
    clickSquare(square){
      let newSquare = this.square;
      newSquare.splice(square, 1,this.turn);
      this.square = newSquare;
      this.confirmWinner(newSquare);
    },
    confirmWinner(newSquare){
      for (let index = 0; index < this.winningPositions.length; index++) {
        const [a,b,c] = this.winningPositions[index];
        if (newSquare[a] && newSquare[a] === newSquare[b] && newSquare[a] === newSquare[c]) {
          this.endGame(newSquare[a], this.winningPositions[index]);
          this.winner = "Winner "+newSquare[a]+" !";
          return
          
        }
      }
      if (!newSquare.includes(null)) {
        this.endGame(null, Array.from(Array(10).keys()));
        this.winner = 'TIE!';
        return
      }
      this.turn = (this.turn === 'X' ? 'O' : 'X');

    },
    endGame(winningTurn, winningPositions){
      this.turn = null;
      if (winningTurn !== null) {
        this.score[winningTurn] += 1; 
      }
      this.winningSquare = winningPositions;
      setTimeout(() => {
        this.reset();
      }, 2000);
    },
    reset(){
      this.turn = "X";
      this.square = Array(9).fill(null);
      this.winningSquare = [];
    }
  },
}
</script>

<style>
  .app{
    margin: 0;
    font-family: Helvetica, sans-serif;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #22333B;
  }
  .winnerBox div{
    color: white;
    font-size: 1.5em;
    padding: 10px;
  }
</style>
