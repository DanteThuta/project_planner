<template>
  <div class="home">
    <h1>Home</h1>
    <div v-for="project in projects" :key="project.id">
          <SingleProject :project="project" @delete="deleteProject" @complete="completeProject"></SingleProject>
    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject'
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    SingleProject,
   
  },
  data(){
    return{
      projects:[]
    }
  },
  methods:{
    deleteProject(id){
      this.projects = this.projects.filter(project=>{
        return project.id!=id;
      })
    },
    // find(method) is to Toggle to Done Button without Refreshing the Page
    completeProject(id){
      let findProject = this.projects.find(project=>{
        return project.id === id;
      })  
      findProject.complete =! findProject.complete;
    }
  },
  mounted(){
    fetch('http://localhost:3000/projects')
    .then((response)=>{
      // console.log(response)
      return response.json()
    })
    .then((datas)=>{
      this.projects = datas; 
    })
    .catch(()=>{

    })
  }
}
</script>
