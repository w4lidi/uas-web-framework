<script setup>
let data
// API for get requests
fetch('https://64abc8e39edb4181202e87b6.mockapi.io/akademik/v1/matakuliah', {
  method: 'GET',
  headers: {'content-type':'application/json'},
}).then(res => {
  if (res.ok) {
      return res.json();
  }
  // handle error
}).then(tasks => {
  // Do something with the list of tasks
  console.log(task)
}).catch(error => {
  // handle error
})
</script>

<template>
<div>{{ data }}</div>

</template>