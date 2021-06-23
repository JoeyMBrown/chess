<template>
    <div>
        <div class="numbers"></div>
            <ul>
                <li :key=number v-for="number in numbers">{{ number }}</li>
            </ul>
        <div class="chessBoard"></div>
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
        letters: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>