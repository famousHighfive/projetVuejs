<script setup>
import { computed } from 'vue'
import SingleItem from './SingleItem.vue'

const props = defineProps({
  books: {
    type: Array,
    required: true,
  },
})

const emit = defineEmits(['delete-book', 'toogle-status'])

const totalRead = computed(() => props.books.filter((book) => book.isRead).length)

function deleteBook(id) {
  emit('delete-book', id)
}

function toogleStatus(id) {
  emit('toogle-status', id)
}
</script>

<template>
  <div class="container">
    <div v-if="books.length">
      <SingleItem
        v-for="(book, index) in books"
        :key="book.id"
        :book="book"
        :index="index"
        @delete-book="deleteBook"
        @toogle-statut="toogleStatus"
      />

      <p>Total: {{ books.length }}</p>
      <p>Lu: {{ totalRead }}</p>
    </div>
    <p v-else>Aucun enregistrement❌</p>
  </div>
</template>

<style scoped>
.container {
  margin-block: 1.3rem;
  max-width: 600px;
  margin-inline: auto;
}

.container p {
  font-size: 1.2rem;
  font-family: 'Times New Roman', Times, serif;
  text-align: center;
}
</style>
