<script setup>

const emit = defineEmits(['view'])

const menus = [
    'Home',
    'Book',
    'Users',
    'FormUsers',
    'Orders',
    'Reports',
    'Settings'
]

function goTo(currentMenu){
    // Au clic, jenvoi levenement view au parent avec le nom du menu cliqué
    emit('view', currentMenu)
}
</script>


<template>

<div class="sidebar-container">
    <h1>Dashboard</h1>
    <ul @click="goTo(menu)" v-for="menu in menus" :key="menu">
        <li class="liStyle">{{ menu }}</li>
    </ul>
</div>

</template>


<style scoped>
.sidebar-container{
    font-family: 'Times New Roman', Times, serif;
    background-color: rgb(34, 36, 48);
    color: white;
    height: 100vh;
    padding: 2rem 1rem;
}

.sidebar-container h1{
    padding-left: 2rem;
}

ul{
    list-style: none;
}

.liStyle{
    background-color: #fff;
    color: black;
    padding: 0.2rem;
    border-radius: 5px;
    cursor: pointer;
}

</style>