<template>
  <div class="home">
    <h1>Home</h1>
    <div v-for="project in projects" :key="project.id">
          <SingleProject :project="project" @delete="deleteProject"></SingleProject>
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
