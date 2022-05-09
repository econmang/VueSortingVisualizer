<template>
    <div id="selections">
      <label for="algos">Select Sorting Algorithm: </label>&nbsp;
      <select id="algos">
        <option value="bubble">Bubble Sort</option>
        <option value="insertion">Insertion Sort</option>
      </select>
      <br><br>
      <label for="arraySize">Select Array Size: </label>&nbsp;
      <select @input="updateArraySize" id="arraySize" placeholder="Select Size">
        <option value="5">5</option>
        <option value="10">10</option>
        <option value="25">25</option>
        <option value="50">50</option>
        <option value="100">100</option>
      </select>
      <br><br>
      <button id="sortButton" v-on:click="runSort()">Sort!</button>
      <br><br>
      <br><br>
    </div>

    <div id="container">
      <div class="bar" v-for="(number,index) in array" :key="index" :style="{ height: number + 'px' }"></div> 
    </div>
</template>

<script>
import sortingAlgos from './SortingAlgos'
export default {
  name: 'VisualSorter',
  data() {
    return {
      arrayLen: 5,
      array: []
    }
  },
  methods: {
    updateArraySize(e) {
      this.arrayLen = e.target.value
    },
    genRandNum() {
     return Math.floor(Math.random() * 500) + 50;
    },
    fillArray() {
      this.array = [] //empty array
      for (var i = 0; i < this.arrayLen; i++) {
        this.array.push(this.genRandNum())
      }
    },
    async runSort() {
      let algos = document.getElementById("algos")
      let arraySize = document.getElementById("arraySize")
      let sortButton = document.getElementById("sortButton")
      this.fillArray();
      
      algos.disabled = true;
      arraySize.disabled = true;
      sortButton.disabled = true;

      // await to ensure components stay disabled until sort is completed
      if (algos.value === "bubble") {
        await sortingAlgos.bubbleSort(this.array, this.arrayLen);
      } else if (algos.value === "insertion") {
        await sortingAlgos.insertionSort(this.array, this.arrayLen); 
      }

      algos.disabled = false;
      arraySize.disabled = false;
      sortButton.disabled = false;
    },
  }
}
</script>

<style scoped>
#selections {
  color: black;
  font-size: 20px;
  font-weight: bold;
}
.container {
  position: fixed;
  left: 100px;
  height: 800px;
}
.bar {
  background-color: black;
  display: inline-block;
  width: 8px;
  margin: 0 5px;
  transition: ;
}
</style>
