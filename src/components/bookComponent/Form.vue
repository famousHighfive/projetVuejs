<script setup>
import { ref } from 'vue';
const emit = defineEmits(['submit'])

// Declaration de variable
const title = ref()
const author = ref()
const date = ref()
const category = ref()


let id = 1  // initialisation d'un ID

function submitForm(){

    // Verification des input valide
     if(title.value.trim() === '') return
     if(author.value.trim() === '') return
     if(date.value === '') return
     if(category.value.trim() === '') return

    //  Envoi des données par emit pour laffichage 
    emit('submit', {
        id: id++,
        title: title.value.trim(),
        author: author.value.trim(),
        date: date.value,
        category: category.value.trim(),
        isRead: false
     })

    //  Reinitialiser les champs
     title.value = ''
     author.value = ''
     date.value = ''
     category.value = ''
     
}


</script>


<template>

    <div class="form-container">
        <form class="form" @submit.prevent="submitForm">
            <input type="text" v-model="title" placeholder="Titre">
            <input type="text" v-model="author" placeholder="Auteur">
            <input type="number" v-model="date" placeholder="Année">
            <input type="text" v-model="category" placeholder="Categorie">
            <button type="submit">Ajouter</button>
        </form>
    </div>

</template>


<style scoped>
.form{
    display: flex;
    justify-content: center;
    gap: 1rem;
}

.form input, button{
    padding: 0.6rem;
    border-radius: 8px;
}
</style>