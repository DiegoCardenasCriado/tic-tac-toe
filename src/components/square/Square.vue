<template>
  <div :class="style" @click="clickSquare">
    
  </div>
</template>

<script>
export default {
  name: 'Square',
  props: {
    value: Array,
    turn: String,
    position: null,
    winningSquare: Boolean
  },
  data() {

    return {
      style: {
        square: true,
        squareX: false,
        squareO: false,
        winner: false
      }
    }
  },
    updated() {
      if (this.value === null) {
         this.style.squareX=false;
         this.style.squareO=false;
      }
      this.style.winner = this.winningSquare;
  },
  methods: {
    clickSquare(){
      if(this.turn !== null && this.value === null){
        //asignamos la clase ya sea para el circulo o la x
        if ((this.turn === "X")) {
          this.style.squareX=true;
        }else if ((this.turn ==="O")) {
          this.style.squareO=true;
        }
        console.log("Squere.vue[39] - clickSquare => entro al IF")
        this.$emit('clickSquare', this.position)
      }else{
        console.log("Squere.vue[42] - clickSquare => no entro al IF")

      }

    }
  },
}
</script>
<style>
    .square{
        width: 155px;
        height: 155px;
        background-color: #848484;
        margin: 5px;
        transition: all .2s;
        border-radius: 0%;
        clip-path: polygon(20% 0%, 0 0, 0 52%, 0 100%, 20% 100%, 49% 100%, 100% 100%, 100% 80%, 100% 53%, 100% 0, 80% 0%, 56% 0);;
    }
    .squareX{
      background-color: #CD493A;
      clip-path: polygon(20% 0%, 0% 20%, 30% 50%, 0% 80%, 20% 100%, 50% 70%, 80% 100%, 100% 80%, 70% 50%, 100% 20%, 80% 0%, 50% 30%);
    }
    .squareO{
      background-color: #4392F1;
      border-radius: 50%;
      }
    .squareX.winner{
      animation: x-winner-animation infinite 1.5s ease-in-out;

    }
    @keyframes x-winner-animation {
      from {
        transform: rotate(0deg);
      }
      to {
        transform: rotate(360deg);
      }
    }

    .squareO.winner{
      animation: o-winner-animation infinite .5s ease-in-out;
      
    }

    @keyframes o-winner-animation {
      0% {border-radius: 50%;}
      50% {border-radius: 0%;}
      100% {border-radius: 50%;} 
    }

    @media (min-width: 300px){
      .square{
          width: 80px;
          height: 80px;
          margin: 2.5px;
      }
    }
    @media (min-width: 400px){
      .square{
          width: 100px;
          height: 100px;
          margin: 3px;
      }
    }
    @media (min-width: 600px){
      .square{
          width: 120px;
          height: 120px;
          margin: 3px;
      }
    }
    @media (min-width: 700px){
      .square{
          width: 150px;
          height: 150px;
          margin: 3px;
      }
    }     
</style>