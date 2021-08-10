<template>
    <div class="project">
        
       <div class="flexing">
           <div>
               <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
                <p v-if="showDetail">{{project.detail}}</p>
           </div>
           <div>
               <span class="material-icons">
                delete
                </span>
                <span class="material-icons">
                edit
                </span>
                <span class="material-icons">
                done_outline
                </span>
           </div>
       </div>
    </div>
    
</template>

<script>
export default {
    data(){
        return{
            showDetail:false,
        }
    },
    props: ['project'],
    methods:{
        // showDetail(){
        //     this.showDetail = true;
        // }
    }
}

</script>

<style>

    body{
        background-color: #272727;
        
    }
    .project{
        padding: 20px;
        background-color: #f9f9f9;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        margin: 10px;
        border-left: 4px solid crimson;
        border-radius: 7px;
    }

    .flexing{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    span{
        margin-left: 15px;
    }

    span:hover{
        cursor: pointer;
        color: #777;
    }

    h3{
        color: indianred;
        cursor: pointer;
    }
</style>