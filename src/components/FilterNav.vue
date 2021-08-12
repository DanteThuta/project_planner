<template>

    <div class="filter-nav">
            <button @click="filterBy('all')" :class="{active : current==='all'}">All</button>
            <button @click="filterBy('complete')" :class="{active : current==='complete'}">Complete</button>
            <button @click="filterBy('ongoing')" :class="{active : current==='ongoing'}">Ongoing</button>
    </div>
  
</template>

<script>
export default {
    props : ['current'],
    methods:{
        filterBy(value){
            //emitting value to Home page for three conditions
            this.$emit("filterValue",value)
        }
    }
}
</script>

<style>
    .filter-nav button{
    background: none;
    border: none;
    color: #bbb;
    outline: none;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    margin-bottom: 20px;
    letter-spacing: 1px;
    font-weight: bold;
    cursor: pointer;

    
}
  
    /* need to put together to Work?  */
    button.active{
        color:lightcoral;
        border: 2px solid lightcoral;
        border-color: lightcoral;
        font-size: 14px;

       
        /* opacity: 0; */
    }
</style>