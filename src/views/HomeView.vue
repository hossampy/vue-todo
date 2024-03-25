<template>
  <div class="home">
    <Filternav :currnet="currnet"  @filterchange="currnet=$event" />
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
        <SingleProject :proj="project" @deleted="handeldeleted" />
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import SingleProject from "../components/SingleProject.vue"
import Filternav from "../components/Filternav.vue"
export default {
  name: 'HomeView',
  components: {
   SingleProject,
    Filternav
  },
  data(){
    return{
      projects:[],
      currnet :'all',
    }
  }
  ,
  mounted(){
    fetch('http://localhost:3000/projects')
    .then(res=>res.json())
    .then(data=>this.projects = data)
    .catch(err=>console.log(err.message))
  },
  methods:{
    handeldeleted(id){
      this.projects =  this.projects.filter((project)=>{
        return project.id !==id
      })
    },
    
  }
}
</script>
