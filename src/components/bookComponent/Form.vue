<script setup>
import { reactive } from 'vue'
const emit = defineEmits(['add-book'])

// Declaration de variable
// const title = ref()
// const author = ref()
// const date = ref()
// const category = ref()

// Bonne methode car ill y avait trop de ref
const form = reactive({
  title: '',
  author: '',
  date: '',
  category: '',
})

// let id = 1  // initialisation d'un ID
// L’enfant ne gère jamais les IDs

function submitForm() {
  // Verification des input valide
  // if (title.value.trim() === '') return
  // if (author.value.trim() === '') return
  // if (date.value === '') return
  // if (category.value.trim() === '') return

  // Verification des input valide recommande en prod
  if (!form.title.trim() || !form.author.trim() || !form.date || !form.category.trim()) return

  //  Envoi des données par emit pour laffichage
  // emit('add-book', {
  //     id: id++,
  //     title: title.value.trim(),
  //     author: author.value.trim(),
  //     date: date.value,
  //     category: category.value.trim(),
  //     isRead: false
  // })

  emit('add-book', { ...form })

  //  Reinitialiser les champs
  form.title = ''
  form.author = ''
  form.date = ''
  form.category = ''
}
</script>

<template>
  <div class="form-container">
    <form class="form" @submit.prevent="submitForm">
      <input type="text" v-model="form.title" placeholder="Titre" />
      <input type="text" v-model="form.author" placeholder="Auteur" />
      <input type="number" v-model="form.date" placeholder="Année" />
      <input type="text" v-model="form.category" placeholder="Categorie" />
      <button type="submit">Ajouter</button>
    </form>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-wrap: wrap;
  /* justify-content: center; */
  gap: 1rem;
}

.form input,
button {
  padding: 0.6rem;
  border-radius: 8px;
}
</style>
