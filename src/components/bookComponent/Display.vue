<script setup>
import { computed } from 'vue';
import SingleItem from './SingleItem.vue';

const props = defineProps({
    data: Array
})

const emit = defineEmits(['delete', 'status'])

function goDelete(id){
    emit('delete', id)
}

function goStatus(data){
    emit('status', data)
}

const totalLu = computed(() => props.data.filter(t => t.isRead == true).length)

</script>


<template>

<div class="container">
    <div v-if="data.length">
        <SingleItem v-for="(dat, index) in data" :key="dat.id" :datas="dat, index" @delete="goDelete" @statut="goStatus" />

        <p>Total: {{ data.length }}</p>
        <p>Lu: {{ totalLu }}</p>
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