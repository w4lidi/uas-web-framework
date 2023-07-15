<template>
    <div v-for="matkuli in matkul" :key="matkuli.id" class="flex flex-wrap m-1 justify-center">
        <div v-if= true >
            <div class=" mb-1 m-1 p-1 border flex-col rounded border-gray-400">
        <div class="text-center text-gray-900 font-bold text-xl mb-2">{{dosen }},{{  }}</div>
    <p  class="text-center text-gray-700 text-base">Prodi : {{  }} {{ matkuli.id }} {{ i}}</p>
    <p class="text-center text-gray-700 text-base">id : {{  }}</p>
    <p class="text-center text-gray-700 text-base">Matkul : {{ c() }} {{  }}</p>
    <!-- <p class="text-center text-gray-700 text-base">dosen : {{ dosen }}</p> -->
    <div  class="flex justify-center">
        <button class="bg-blue-500 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Edit</button>
        <button class="bg-red-600 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Delete</button>
    </div>
    </div>
        </div>
  
  </div>
  <div>{{ c0() }}xx</div>

</template>


<script setup >
import { text } from 'stream/consumers';

let i =0
const c = () =>{i++}
const c0 = () =>{i = 0}
const { data: datadosen } = await useFetch('https://64abc8e39edb4181202e87b6.mockapi.io/akademik/v1/matakuliah')
   const props = defineProps({
        akadata:{
            type:Object,
        }
    })
const url ='https://64abc8e39edb4181202e87b6.mockapi.io/akademik/v1/matakuliah/'
    let dosen = []
let matkul = props.akadata
for(let x in matkul){
    let strurl = url + x + "/dosen"
    //dosen.push(await useFetch( strurl.toString()))

    await fetch(strurl.toString()).then((response) => {
        if(response.ok){
            return response.text();
        }
}).then(
    console.log(text)
);
};


let x = 23 
let nmdosen = ""
//console.log(dosen[1][error])
//let prodi = Object(nmdosen[0][0][0]).length




</script>