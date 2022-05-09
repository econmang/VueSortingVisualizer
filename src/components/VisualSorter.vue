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
    runSort() {
      this.fillArray();
      
      document.getElementById("algos").disabled = true;
      document.getElementById("arraySize").disabled = true;
      document.getElementById("sortButton").disabled = true;

      this.bubbleSort();

      document.getElementById("algos").disabled = false;
      document.getElementById("arraySize").disabled = false;
      document.getElementById("sortButton").disabled = false;
    },
	async bubbleSort() {
      let sorted = false;
      let counter = 1;
      while (!sorted) {
        sorted = true;
        for(let i = 0; i < this.arrayLen - counter; i++) {
          if (this.array[i] > this.array[i+1]) {
            sorted = false; 
			let temp = this.array[i]
			this.array[i] = this.array[i+1]
			this.array[i+1] = temp
          }
        }
		counter++;
      }
	}
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
}
</style>
