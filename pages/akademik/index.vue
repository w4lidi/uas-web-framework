<script setup>
const url = 'https://64abc8e39edb4181202e87b6.mockapi.io/akademik/v1/matakuliah/'

  let { data: matakuliah } = await useFetch(url)
  let datamatkul = matakuliah
  const datas = ref('')


  const add = ref(true) 
  const btn = ref(false) 


 
function da(){
  let { data: matakuliah } =  useFetch(url)
  datamatkul = matakuliah
}
 let matkulin 
 let sks 
function save(){
 
  const newTask = {
  matakuliah: matkulin,
  sks: sks,
};

useFetch(url, {
  method: 'POST',
  headers: {'content-type':'application/json'},
  // Send your data in the request body as JSON
  body: JSON.stringify(newTask)
}).then(res => {
  if (res.ok) {
      return res.json();
      
  }
  // handle error
}).then(task => {
  // do something with the new task
  location.reload()
}).catch(error => {
  // handle error
})
}






</script>

<template>
<Header></Header>
<card></card>
  <div class="flex flex-wrap m-1 justify-center">
    <div v-for="(matakuliah, index) in datamatkul" class=" mb-1 m-1 p-1 border flex-col rounded border-gray-400">
      <matkulCard :matkul=datamatkul[index].matakuliah :sks=datamatkul[index].sks :id="datamatkul[index].id" />
    </div>
    <div v-if="add">
      <button class="bg-green-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center" @click='add = !add'>
  
  <span>Add Data</span>
</button>
    </div>
    <div v-else class=" mb-1 m-1 p-1 border flex-col rounded border-gray-400" >
        <p class="text-center">Tambah Data Baru {{ matkulin }} : {{sks}}</p>
        <label for="matkul">Matkul: </label><input id="matkul" v-model="matkulin" class="border rounded" :disabled="btn" placeholder="edit me" />
        <label for="sks">SKS: </label><input id="sks" type="number" v-model="sks" class="border rounded" :disabled="btn" placeholder="edit me" />
        <div class="flex justify-center">
            <button class="bg-blue-500 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" :disabled="btn" @click="() => {save(), btn = true}">save</button>
            <button class="bg-blue-100 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" :disabled="btn" @click='add = !add'>hide</button>
        </div>
    </div>
    
    </div>
  <div>{{ add }}  </div>
  <div>{{ btn }}  </div>
</template>
