<script setup>
import { computed, ref } from 'vue'
import SideBar from './layouts/SideBar.vue'
import Home from './main/Home.vue'
import Book from './main/Book.vue'
import Users from './main/Users.vue'
import FormUsers from './main/FormUsers.vue'
import Orders from './main/Orders.vue'
import Reports from './main/Reports.vue'
import Settings from './main/Settings.vue'

const pages = { Home, Book, Users, FormUsers, Orders, Reports, Settings }

const currentPage = ref('Home') // Gestion de l'Etat

const currentComponent = computed(() => pages[currentPage.value])

function gotoPage(page) {
  currentPage.value = page.component
}
</script>

<template>
  <div class="container">
    <header>
      <SideBar @view="gotoPage" />
    </header>
    <main>
      <component :is="currentComponent" />
    </main>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 240px 1fr;
}

@media screen and (max-width: 768px) {
  .container {
    grid-template-columns: 1fr;
  }
}
</style>
