<template>
    <nav class="filter">
        <button @click="updatefilter('all')" :class="{ active: currnet==='all' }"> view all</button>
        <button @click="updatefilter('completed')" :class="{ active: currnet === 'completed' }"> completed</button>
        <button @click="updatefilter('ongoing')" :class="{ active: currnet === 'ongoing ' }"> ongoing </button>

    </nav>
</template>

<script>
export default {
    props: ['currnet'],
    data(){
        return{

        }
    },
    methods:{
        updatefilter(by){
            this.$emit('filterchange',by)
        }
    }

}
</script>

<style>
.filter button {
    margin-left: 80px;
    background: none;
    border: none;
    color: #bbb;
    outline: none;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    letter-spacing: 1px;
    font-weight: bold;
    cursor: pointer;
    align-items: center;
}

button.active {
    color: #5ff787;
}
</style>