<template>
  <h1>Edit Project {{id}}</h1>

  <form @submit.prevent="addProject">
        <label for="">Edit Project Title</label>
        <input type="text" v-model="title"/>

        <label for="">Edit Project Detail</label>
        <input type="text" v-model="detail"/>

        <button>
            Edit
        </button>
    </form>
</template>

<script>
export default {
    props: ["id"],
    data(){
        return{
            title: "",
            detail: "",
        }
    },
    //Used Mounted to show the Recent data on the Edit Page
    mounted(){
        // console.log('http://localhost:3000/projects/'+ this.id);
        fetch('http://localhost:3000/projects/'+ this.id)
        .then((res)=>{
            return res.json();
        })
        //then again to retrieve the Edit data from above json Data
        .then((datas)=>{
            this.title = datas.title;
            this.detail = datas.detail;
        })
        .catch((err)=>{
            console.log(err);
        })
    }
    
}
</script>

<style>

</style>