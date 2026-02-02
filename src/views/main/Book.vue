<script setup>
import Display from '@/components/bookComponent/Display.vue'
import Form from '@/components/bookComponent/Form.vue'
import { ref } from 'vue'

let books = ref([])

// Toujours travailler avec id, jamais l’objet entier

// ajouter un livre
// function addBook(book) {
//     books.value.push(book)
// }
function addBook(book) {
  books.value.push({
    ...book,
    id: Date.now(),
    isRead: false,
  })
}

// supprimer un livre
function deleteBook(id) {
  books.value = books.value.filter((book) => book.id !== id)
}

// changer le statut lu / non lu
// function toogleStatus(data) {
//     data.isRead = !data.isRead  // On ne mute jamais directement, on travaille via l’état central.
// }
function toogleStatus(id) {
  books.value = books.value.map((book) =>
    book.id === id ? { ...book, isRead: !book.isRead } : book,
  )
}
</script>

<template>
  <header class="header">
    <h1>GESTION DE LIVRES</h1>
  </header>

  <main>
    <div class="container">
      <Form @add-book="addBook" />

      <Display :books="books" @delete-book="deleteBook" @toogle-status="toogleStatus" />
    </div>
  </main>

  <footer></footer>
</template>

<style scoped>
.header {
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
