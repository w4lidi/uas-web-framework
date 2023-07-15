

<template>
        <div class="text-center text-gray-900 font-bold text-xl mb-2"  >{{ matkul }}</div>
        <p class="text-center text-gray-700 text-base">SKS : {{ sks }}</p>
        <div class="flex justify-center">
            <button class="bg-blue-500 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" >Edit</button>
            <button class="bg-red-600 m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="$emit(rm( id ))">Delete</button>
        </div>

        


</template>


<script>
export default{
    data(){
        return{
            url : 'https://64abc8e39edb4181202e87b6.mockapi.io/akademik/v1/matakuliah/',
        }
        
    },
    props:{
        matkul : {
            type: String,
            default: "Nama Matkul"
        },
        sks : {
            type: Number,
            default: 0},
        id : {
            type: Number,
            default: 0}
    },
    methods:{
         rm(id){

            useFetch(this.url + id.toString(), {
            method: 'DELETE',
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
    },

         
        
    
}
</script>