<script setup>
import Display from '@/components/bookComponent/Display.vue';
import Form from '@/components/bookComponent/Form.vue';
import { ref } from 'vue';

let myDatas = ref([]);

function getData(dat){
    myDatas.value.push(dat)    
    console.log(myDatas);
}

function getDelete(id){
    myDatas.value = myDatas.value.filter(t => t.id !== id)
}

function getStatus(data){
    data.isRead = !data.isRead
}

</script>


<template>
    <header>
        <h1>GESTION DE LIVRES</h1>
    </header>

    <main>
        <div class="container">
            <Form @submit="getData" />

            <Display :data="myDatas" @delete="getDelete" @status="getStatus" />
        </div>
    </main>

    <footer></footer>

</template>


<style scoped>
header{
    text-align: center;
    padding: 1rem;
}
.container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 0.5rem;
}
</style>
