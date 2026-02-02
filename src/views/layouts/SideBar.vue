<script setup>
const emit = defineEmits(['view'])

const menus = [
  { label: 'Home', component: 'Home' },
  { label: 'Book', component: 'Book' },
  { label: 'Users', component: 'Users' },
  { label: 'FormUsers', component: 'FormUsers' },
  { label: 'Orders', component: 'Orders' },
  { label: 'Reports', component: 'Reports' },
  { label: 'Settings', component: 'Settings' },
]

function goTo(currentMenu) {
  // Au clic, jenvoi levenement view au parent avec le nom du menu cliqué
  emit('view', currentMenu)
}
</script>

<template>
  <aside class="sidebar-container">
    <h1>Dashboard</h1>

    <ul>
      <li @click="goTo(menu)" v-for="menu in menus" :key="menu.label" class="liStyle">
        {{ menu.component }}
      </li>
    </ul>
  </aside>
</template>

<style scoped>
.sidebar-container {
  font-family: 'Times New Roman', Times, serif;
  background-color: rgb(34, 36, 48);
  color: white;
  min-height: 100vh;
  padding: 2rem 1rem;
}

ul {
  padding: 0;
}

.liStyle {
  list-style: none;
  background-color: #fff;
  color: black;
  padding: 0.6rem;
  margin-bottom: 0.3rem;
  border-radius: 6px;
  cursor: pointer;
}
</style>
