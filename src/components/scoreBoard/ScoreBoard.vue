<template>
  <div class="score-board">
    <div>
        {{scoreX}}
    </div>
    <div>
        {{scoreO}}
    </div>
  </div>
</template>

<script>

export default {
  name: 'ScoreBoard',
  props:{
    scoreX: Number,
    scoreO: Number
  },
}
</script>
<style>
  .score-board{
    width: 420px;
    display: grid;
    grid-auto-flow: column;
    margin-top: 2px;
  }

  .score-board div{
    color: white;
    text-align: center;
    font-size: 2em;
    padding: 5px;
    font-weight: bold;
    background-color: #4392F1;
  }

    .score-board div:first-child{
    background-color: #CD493A;
  }

    @media (min-width: 300px){
      .score-board{
        width: 250px;
        margin-top: 3px;
      }
      .score-board div{
      font-size: 1.5em;
      padding: 2px;
      }      
    }

    @media (min-width: 400px){
      .score-board{
        width: 311px;
        margin-top: 3px;
      }
      .score-board div{
      font-size: 1.5em;
      padding: 3px;

      }      
    }
    @media (min-width: 600px){
      .score-board{
        width: 375px;
        margin-top: 3px;
      }
      .score-board div{
      font-size: 2em;
      padding: 3px;

      }      
    }
    @media (min-width: 700px){
      .score-board{
        width: 465px;
        margin-top: 3px;
      }
      .score-board div{
      font-size: 2em;
      padding: 3px;

      }      
    }
      
</style>