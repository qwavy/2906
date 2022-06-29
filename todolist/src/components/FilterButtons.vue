<template>  
    <button @click="onAll">all</button>
    <button @click="onImportant">important</button>
    <button @click="onDone">Done</button>

</template>
<script>
export default {
    emits:['filteredFunc','showAll'],
    props:[''],
    methods:{
        onAll(){
            this.$emit("showAll")
            alert('asd')
        },
        onImportant(){
            alert('sa')
        },
        onDone(){
            
        }
    }
}
</script>