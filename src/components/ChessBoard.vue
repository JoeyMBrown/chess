<template>
    <div>
        <div class="chessBoardUi">
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
.chessBoardUi {
    display: flex;
    justify-content: center;
    align-items:center;
    padding: 0 20%;
    margin-top: 2%;
}
.numbers {
    margin-right: 1%;
}
.numbers li {
    display: flex;
    align-items: center;
    height: 11.5vh;
}
.chessBoard {
    display: flex;
    flex-flow: row wrap-reverse;
    justify-content: center;
    border: 5px solid black;
}
.chessBoard li {
    display:flex;
    align-items: flex-start;
    justify-content: flex-end;
}
.black {
    background-color: black;
}
.white {
    background-color: white;
}
.square {
    width: 12.5%;
    height: 11.5vh;
}
.letters {
    padding: 0 21% 0 21.4%;
}
.letters ul{
    display: flex;
    width: 100%;
    margin: 0 auto;
    align-items:center;
}
.letters li{
    display:flex;
    align-items: center;
    justify-content: center;
    width: 12.5%;
}
</style>