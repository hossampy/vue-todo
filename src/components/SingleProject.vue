<template>
  <div class="project" :class="{complete : proj.complete==true}">
    <div class="action">
      <h3 @click="toggleDetails">{{proj.title}}</h3>
      <div class="icons">
        <span @click="toggledone" class="material-icons done">done</span>
        <router-link :to="{ name: 'EditProject', params: { id: proj.id } }"> 
             <span class="material-icons edit">edit</span>
        </router-link>
        <span @click="deleteProject" class="material-icons delete">delete</span>
      </div>
    </div>
    <div v-if="showdetails" class="details">
      <p>{{ proj.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['proj'],
  data() {
    return {
      showdetails: false,
      baseUri: 'http://localhost:3000/projects/'
    }
  },
  methods: {
    toggleDetails() {
      this.showdetails = !this.showdetails;
    },
    async deleteProject() {
      try {
        const response = await fetch(this.baseUri + this.proj.id, { method: 'DELETE' });
        if (response.ok) {
         
          this.$emit('deleted', this.proj.id); 
        } else {
          console.error('Failed to delete project:', response.statusText);
        }
      } catch (error) {
        console.error('Error deleting project:', error);
      }
    } ,
     async toggledone() {
        try{  const response = await fetch(this.baseUri +this.proj.id,{
            method:'PATCH',
            headers:{
                'Content-Type': 'application/json'
            },
            body:JSON.stringify({
                complete : !this.proj.complete
            })

             });
              if (response.ok) {
                this.proj.complete = !this.proj.complete; 
                this.$emit('complete', this.proj.id); 
              }else {
                 console.error('Failed to update completion status:', response.statusText);
            }}
       
            catch (error) {
              console.error('Error updating completion status:', error);
                     }

     }
    
}
  
}
</script>

<style>
.project{
    margin: 20px auto;
    background: rgb(255, 255, 255);
    padding: 10px 20px;
    border-radius: 10px;
    box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
    border-left: 4px solid #f52d2d;
}
h3{
    cursor: pointer;
}
.action{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.material-icons{
    margin: 5px;
    cursor: pointer;
}
.material-icons.delete:hover{
    color: rgb(255, 48, 48);
}
.material-icons.done:hover{
    color: rgb(76, 255, 48);
}
.material-icons.edit:hover{
    color: rgb(224, 48, 255);
}
.complete{
    border-left: 4px solid #5af173;
    text-decoration: line-through;
    opacity: 50%;
}
</style>