<script>
export default {
  bubbleSort: async function(array, arrayLen) {
    let sorted = false;
	let counter = 1;
	while (!sorted) {
      sorted = true;
      for(let i = 0; i < arrayLen - counter; i++) {
        if (array[i] > array[i+1]) {
          sorted = false;
          let temp = array[i]
          array[i] = array[i+1]
          array[i+1] = temp
          await this.sleep(); 
        }
    }
      counter++;
    }
  },
  // TODO: update with insertion sort algo; currently just copy of bubbleSort
  insertionSort: async function(array, arrayLen) {
    let sorted = false;
	let counter = 1;
	while (!sorted) {
      sorted = true;
      for(let i = 0; i < arrayLen - counter; i++) {
        if (array[i] > array[i+1]) {
          sorted = false;
          let temp = array[i]
          array[i] = array[i+1]
          array[i+1] = temp
          await this.sleep(); 
        }
    }
      counter++;
    }
  },
  // used to show animation/movement of values
  sleep: function() {
    return new Promise((resolve => setTimeout(resolve,10)))
  },
  name: 'sortingAlgos',
}
</script>
