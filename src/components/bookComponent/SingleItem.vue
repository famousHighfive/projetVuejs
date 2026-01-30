<script setup>
const props = defineProps({
    datas: Object,
    index:Number
})

const emit = defineEmits(['delete'])

function deleteItem(){
    emit('delete', props.datas.id)
}
</script>


<template>

        <div class="item">
            <span>{{ index+1 }}</span>
            <span>{{ datas.title }}</span>
            <span>{{ datas.author }}</span>
            <span><span class="read">A Lire</span><span class="hasRead">Marquer lu</span></span>
            <button @click="deleteItem" class="btnDel">❌</button>
        </div>

</template>


<style scoped>
.item{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1.6rem;
    border: 1px solid;
    border-radius: 5px;
    padding: 0.6rem;
    margin-top: 5px;
}

.read{
    background-color: gray;
    border: 1px solid;
    padding: 3px;
    color: white;
    cursor: pointer;
}

.hasRead{
    background-color: fff;
    border: 1px solid;
    padding: 3px;
    cursor: pointer;
}

.btnDel{
    cursor: pointer;
}
</style>