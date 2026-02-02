<script setup>
const props = defineProps({
  book: {
    type: Object,
    required: true,
  },
  index: Number,
})

const emit = defineEmits(['delete-book', 'toogle-statut'])

function deleteItem() {
  emit('delete-book', props.book.id)
}

function toogleRead() {
  emit('toogle-statut', props.book.id)
}
</script>

<template>
  <div class="item" :class="{ active: book.isRead }">
    <span :class="{ underline: book.isRead }"
      >{{ index + 1 }}. {{ book.title }} - {{ book.author }}</span
    >
    <div>
      <span class="read">{{ book.isRead ? 'Lu' : 'A lire' }}</span
      ><button @click="toogleRead" class="hasRead">
        {{ book.isRead ? 'Marquer non Lu' : 'Marquer Lu' }}
      </button>
    </div>
    <button @click="deleteItem" class="btnDel">❌</button>
  </div>
</template>

<style scoped>
.item {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.6rem;
  border: 1px solid;
  border-radius: 5px;
  padding: 0.6rem;
  margin-top: 5px;
}

.read {
  background-color: gray;
  padding: 3px;
  color: white;
}

.hasRead {
  border: 1px solid;
  cursor: pointer;
}

.btnDel {
  cursor: pointer;
}

.active {
  background-color: rgb(197, 240, 223);
}

.underline {
  text-decoration: line-through;
}
</style>
