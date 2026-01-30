<script setup>
import SingleItem from './SingleItem.vue';

const props = defineProps({
    data: Array
})

const emit = defineEmits(['delete'])

function goDelete(id){
    emit('delete', id)
}

</script>


<template>

<div class="container">
    <div v-if="data.length">
        <SingleItem v-for="(dat, index) in data" :key="dat.id" :datas="dat, index" @delete="goDelete" />
    </div>
    <p v-else>Aucun enregistrement❌</p>
</div>

</template>


<style scoped>
.container{
    margin-block: 1.3rem;
    width: 40%;
    margin-inline: auto;
}

.container p{
    font-size: 1.6rem;
    text-align: center;
}
</style>