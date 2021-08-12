<template>
    <div class="project" :class="{complete:project.complete}">
        
       <div class="flexing">
           <div>
               <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
                <p v-if="showDetail">{{project.detail}}</p>
                <!-- {{project.complete}} -->
           </div>
           <div>
               <span class="material-icons" @click="deleteProject">
                delete
                </span>
                <span class="material-icons">
                edit
                </span>
                <span class="material-icons" @click="completeProject">
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
            api : 'http://localhost:3000/projects/',
        }
    },
    props: ['project'],
    methods:{
        deleteProject(){
            // Making a Variable for api link and project ID
            let delPrj = this.api + this.project.id;
            
            fetch(delPrj,{method:"DELETE"})//code to Delete JSon data from server
            .then(()=>{
                //Id must be carried to Home page for Web Page Deletion
                this.$emit("delete",this.project.id)
            })
            .catch((err)=>{
                console.log(err);
            })
            // console.log(delPrj);
        },
        completeProject(){
            let updateCompleteProject = this.api + this.project.id;
            fetch(updateCompleteProject,{
                method:"PATCH",
                headers:{
                    "Content-Type" : "application/json"
                },
                body:JSON.stringify(
                    {
                        complete: !this.project.complete
                    }
                )
            })
            .then(()=>{
                this.$emit("complete",this.project.id)
            })
            .catch((err)=>{
                console.log(err);
            })
        }
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

    .complete{
        border-left-color: green;
    }
</style>