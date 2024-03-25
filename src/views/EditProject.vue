<template>
  <form @submit.prevent="updateProject">
    <label>Title</label>
    <input type="text" v-model="title" required>
    <label>Details</label>
    <textarea v-model="details" required></textarea>
    <button type="submit">Update Project</button>
  </form>
</template>

<script>
export default {
  props: ['id'],
  data() {
    return {
      title: '',
      details: '',
      uri: 'http://localhost:3000/projects/' + this.id
    }
  },
  async mounted() {
    await this.fetchProject();
  },
  methods: {
    async fetchProject() {
      try {
        const response = await fetch(this.uri);
        const data = await response.json();
        this.title = data.title;
        this.details = data.details;
      } catch (error) {
        console.error('Error fetching project:', error);
      }
    },
    async updateProject() {
      const projectData = {
        title: this.title,
        details: this.details
      };

      try {
        const response = await fetch(this.uri, {
          method: 'PATCH', 
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify(projectData)
        });

        if (response.ok) {
          console.log('Project updated successfully!');
          this.$router.push('/')
          
        } else {
          console.error('Failed to update project:', response.statusText);
        }
      } catch (error) {
        console.error('Error updating project:', error);
      }
    }
  }
}
</script>

<style>
form{
    background: white;
    padding: 20px;
    border-radius: 10px;
    border-radius: 10px;
}
label{
    display: block;
    color: #51f588;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 20px 0 10 0;
}
input{
    padding: 10px;
    border: 0;
    border-bottom: 1px solid #ddd;
    width: 100%;
    box-sizing: border-box;
    margin-bottom: 20px;
}
textarea{
     padding: 10px;
    border: 0;
    border-bottom: 1px solid #ddd;
    width: 100%;
    height: 100px;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
   
}
form button{
    display: block;
    margin: 20px auto 0;
    background: #51f588;
    padding: 15px;
    border: 0;
    border-radius: 10px;
    font-size: 16px;
    color: #ffffff;
    font-weight: bold;
    margin-bottom: 20px;
}
form button:hover{
    color: #ffffff;
     background: #8f53f6;
     
}</style>