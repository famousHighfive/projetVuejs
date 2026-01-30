<script setup>
const props = defineProps({
    datas: Object,
    index: Number
})

const emit = defineEmits(['delete', 'statut'])

function deleteItem() {
    emit('delete', props.datas.id)
}

function toogle(){
    emit('statut', props.datas)
}
</script>


<template>

    <div id="item" :class="datas.isRead? 'active' : ''">
        <span :class="datas.isRead ? 'underline' : ''">{{ index + 1 }} {{ datas.title }} {{ datas.author }}</span>
        <span><span class="read">{{ datas.isRead ? 'Lu' : 'A lire' }}</span><button @click="toogle" class="hasRead" >{{ datas.isRead? 'Marquer non Lu':'Marquer Lu' }}</button></span>
        <button @click="deleteItem" class="btnDel">❌</button>
    </div>

</template>


<style scoped>
#item {
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
    border: 1px solid;
    padding: 3px;
    color: white;
    cursor: pointer;
}

.hasRead {
    background-color: fff;
    border: 1px solid;
    padding: 3px;
    cursor: pointer;
}

.btnDel {
    cursor: pointer;
}

.active{
    background-color: rgb(197, 240, 223);
}

.underline{
    text-decoration: line-through;
}
</style>