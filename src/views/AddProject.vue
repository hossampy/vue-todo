<template>
  <form @submit.prevent="addproject">
    <label >title</label>
    <input type="text" v-model="title" required>
    <label >Details</label>
    <textarea required  v-model="Details "></textarea>
    <button> add project</button>
  </form>
</template>

<script>
export default {
    data(){
        return{
            title:"",
            Details:""
        }
    },
    methods:{
        addproject(){
            console.log(this.title)
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
     
}
</style>