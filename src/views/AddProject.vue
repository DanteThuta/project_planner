<template>
    <h1>Add Project </h1>
    <form action="">
        <label for="">Project Title</label>
        <input type="text"/>

        <label for="">Project Detail</label>
        <input type="text"/>

        <button>
            Add
        </button>
    </form>
  
</template>

<script>
export default {

}
</script>

<style>

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
        padding: 10px;
        border: 0;
        border-radius: 10px
        ;
    }
</style>