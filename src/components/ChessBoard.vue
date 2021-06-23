<template>
    <div>
        <div class="numbers">
            <ul>
                <li :key=number v-for="number in numbers">{{ number }}</li>
            </ul>
        </div>
        <div class="chessContainer">
            <ul class="chessBoard">
                <li :id=letterNumber :key=letterNumber v-for="letterNumber in chessBoardIds">{{ letterNumber }}</li>
            </ul>
        </div>
        <div class="letters">
            <ul>
                <li :key=letter v-for="letter in letters">{{ letter }}</li>
            </ul>
        </div>
    </div>
    
</template>

<script>
export default {
  name: 'ChessBoard',
  data() {
      return {
        numbers: ['1', '2', '3', '4', '5', '6', '7', '8'],
        letters: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'],
        chessBoardIds: [],
        methods: {

        }
    }
  },
  created() {
    //Create all chessboard files
    for(let i = 0; i < this.numbers.length; i++) {
        this.letters.forEach(item => this.chessBoardIds.push(item + this.numbers[i]));
    }
  },
  mounted() {
        let black = true; //true
        let index = 0;
    for(let i = 0; i < this.chessBoardIds.length; i++) {
        let currentSquare = document.getElementById(this.chessBoardIds[i]);
        currentSquare.classList.add('square');

        if(black) {
            currentSquare.classList.add('black');
            black = !black;
            index++;
        } else {
            currentSquare.classList.add('white');
            black = !black;
            index++;
        }

        if(index % 8 === 0 && index != 0) {
            black = !black;
            console.log(black + ' ' + this.chessBoardIds[i]);
        }
    }
    console.log(this.chessBoardIds);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.black {
    background-color: black;
}
.white {
    background-color: white;
}
.square {
    width: 12%;
    height: 10vh;
}

.chessBoard {
    display: flex;
    flex-flow: row wrap-reverse;
    justify-content: center;
}
</style>