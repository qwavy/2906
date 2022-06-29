<template>  
    <button class="{active: value === 'all'}" @click="$emit('change','all')">all</button>
    <button class="{active: value === 'important'}" @click="$emit('change','done')">done</button>
    <button class="{active: value === 'done'}" @click="$emit('change','important')">impor</button>

</template>
<script>
export default {
    emits:['filteredFunc','showAll'],
    props:['value']
}
</script>
<style scoped>
    .active{
        background-color:firebrick 
    }
</style>