<template>
    <h2>{{counter}}</h2>
    <h2>sqaure {{squareCounter}}</h2>
    <button @click="counter++">inc</button>
    <button @click="counter--">dec</button>
</template>

<script>
export default {
    data(){
        return{
            counter: 0

        }
    },
    computed:{
        squareCounter(){
            return this.counter * this.counter
            // return 5
        }
    }
}
</script>