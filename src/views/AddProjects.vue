<template>
  <form  @submit.prevent="handleSubmit">
    <label for="title">Title</label>
    <input type="text" id="title" v-model="title" required>
    <label for="details">Details:</label>
    <textarea v-model="details"  id="details" cols="30" rows="10"></textarea>
    <button>Add Projects</button>
  </form>
</template>

<script>
export default {
data(){
    return{
        title: "",
        details : ""
    }
},
methods:{
    handleSubmit(){
       let project = {
        title : this.title,
        details : this.details,
        complete: false
       }
       fetch('http://localhost:3000/projects',{
        method: 'POST',
        headers:{'Content-Type': 'application/json'},
        body: JSON.stringify(project)

       }).then(() => {
        this.$router.push('/')
       }).catch((err) => console.log(err))
    }
}
}
</script>

<style>
form{
    background: white;
    padding:20px;
    border-radius: 20px;
}
label{
    display: block;
    color: #bbb;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 10px;
    margin: 20px 0 10px 0;
}
input{
    padding: 10px;
    border: 0;
    border-bottom: 1px solid #ddd;
    width: 100%;
}
textarea{
    border: 1px solid #ddd;
    padding: 10px;
    width: 100%;
    box-sizing: border-box;
    height: 100px;
}
form button{
    display: block;
    margin: 20px auto 0;
    background: #00ce89;
    color: white;
    padding: 10px;
    border: 0;
    border-radius: 6px;
    font-size: 16px;
}
input:focus , textarea:focus {
  outline: 0.1em solid darkgray;
}
</style>