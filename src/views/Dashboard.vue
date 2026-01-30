<script setup>
import { ref } from 'vue';
import SideBar from './layouts/SideBar.vue';
import Home from './main/Home.vue';
import Book from './main/Book.vue';
import Users from './main/Users.vue';
import FormUsers from './main/FormUsers.vue';
import Orders from './main/Orders.vue';
import Reports from './main/Reports.vue';
import Settings from './main/Settings.vue';

const currentPage = ref('Home')

function gotoPage(val){
    currentPage.value = val;
}


</script>

<template>
  <div class="container">
    <header>
      <SideBar @view="gotoPage" />
    </header>
    <main>
      <Home v-if="currentPage == 'Home'" />
      <Book v-else-if="currentPage == 'Book'"/>
      <Users v-else-if="currentPage == 'Users'"/>
      <FormUsers v-else-if="currentPage == 'FormUsers'"/>
      <Orders v-else-if="currentPage == 'Orders'"/>
      <Reports v-else-if="currentPage == 'Reports'"/>
      <Settings v-else-if="currentPage == 'Settings'"/>
    </main>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 15% 85%;
}
</style>
