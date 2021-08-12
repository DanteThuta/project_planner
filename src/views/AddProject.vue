<template>
    <h1>Add Project </h1>
    <form @submit.prevent="addProject">
        <label for="">Project Title</label>
        <input type="text" v-model="title"/>

        <label for="">Project Detail</label>
        <input type="text" v-model="detail"/>

        <button>
            Add
        </button>
    </form>
  
</template>

<script>
export default {
    data(){
        return{
            title:'',
            detail:'',
        }
    },
    methods:{
        addProject(){
            // console.log(this.title,this.detail);
            fetch('http://localhost:3000/projects',{
                method: "POST",
                headers:{
                    "Content-Type" : "application/json"
                },
                body:JSON.stringify(
                    {
                        title : this.title,
                        detail: this.detail,
                        complete: false   
                    }
                )
            })
            .then(()=>{
                // to redirect to Project Page
                this.$router.push({name:'Home'});
            })
            .catch((err)=>{
                console.log(err);
            })

        }
    }
}
</script>

<style>

    h1{
        color: lightcoral;
    }
    form{
        background-color: #272727;
        padding: 10px;
        border-radius: 10px;

    }

    label{

    display: block;
    color: #bbb;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 20px 0 20px 0;
    text-align: left;
    }

    input{
        padding: 20px;
        border:0;
        border-bottom: 2px solid #bbb;
        width: 100%;
        box-sizing: border-box;

        border-radius: 10px;
    }

    form button{
        display: block;
        margin: 20px auto 0;
        font-size: 16px;

        background-color: #00ce89;
        color: #272727;
        padding: 10px 20px ;
        border: 0;
        border-radius: 10px;
        font-family: sans-serif;
        font-weight: bold;
    }
</style>