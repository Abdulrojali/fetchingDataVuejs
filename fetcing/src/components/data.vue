<script>
import {ref} from 'vue'
export default{
    setup(){
        const datas=ref(null)
        const datafetching=async ()=>{
            await fetch('https://jsonplaceholder.typicode.com/photos/')
            .then(Response=>Response.json())
            .then(data=>datas.value=data)
            .catch(err=>console.log(err))
        }
        return {datas,datafetching}
    },
    mounted(){
        this.datafetching()
    }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-4 d-flex flex-column gap-2 p-2" v-for="(data,index) in datas" :key="index">
                <img :src="data.url" class="img-fluid" alt="">
                <h3 class="h4">{{ data.title }}</h3>
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>