<template>
  <div class="home">
    <h1>Project Lists</h1>
    <FilterNav @filterValue="current=$event" :current="current"></FilterNav>
    <div v-for="project in projects" :key="project.id">
          <SingleProject :project="project" @delete="deleteProject" @complete="completeProject"></SingleProject>
    </div>
  </div>
  {{current}}
</template>

<script>
import FilterNav from '../components/FilterNav'
import SingleProject from '../components/SingleProject'
// @ is an alias to /src


export default {
  name: 'Home',
  components: {
    FilterNav,
    SingleProject,
   
  },
  data(){
    return{
      projects:[],
      current:"all"
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
