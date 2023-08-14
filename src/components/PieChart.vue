
<script setup>
import { onBeforeMount,onMounted, onBeforeUnmount, ref } from 'vue';
const newItem = ref('')
let newPieChart = null
 let dataset = [10,20,30]

onBeforeMount(()=>{
    let dataset = [20,30,50,60]
})
// newPieChart data
const data = {
  labels: [
    'Red',
    'Green',
    'Blue'
  ],
  datasets: [{
    label:'my first dataset',
    data: dataset,
    backgroundColor: [
      'red',
      'green',
      'blue',
      'yellow'
    ] ,
    hoverOffset: 4
  }]
};

const config = {
  type: 'pie',
  data: data,
};

onMounted(()=>{
    const ctx = document.getElementById('chart')
    newPieChart = new Chart(ctx,config)
})


function updateChart(){
    dataset.push(newItem.value)
    newPieChart.data.datasets[0].data = dataset
    newPieChart.update()
    console.log(newItem.value)
}

</script>

<template>
<section class="mt-20">
    <div class="mx-auto w-[400px] h-[400px] bg-gray-400">
        <canvas id="chart"></canvas>

     </div>
  <div class="mt-20">
    <p>{{ newItem }}</p>
    <input type="text" v-model="newItem" class="border border-gray-500 px-2 ">
    <button @click="updateChart()" class="ml-2 px-2 py-0 bg-slate-400 text-black ">Add %</button>
  </div>
</section>
  
</template>

<style scoped>

</style>