<template>
  <form  @submit.prevent="handleSubmit">
    <label for="title">Title</label>
    <input type="text" id="title" v-model="title" required />
    <label for="details">Details:</label>
    <textarea v-model="details" id="details" cols="30" rows="10"></textarea>
    <button>Update Projects</button>
  </form>
</template>
  
  <script>
export default {
  props: ["id"],
  data() {
    return {
      title: "",
      details: "",
        uri: "http://localhost:3000/projects/" + this.id
    };
  },
  mounted() {
    fetch(this.uri)
      .then((res) => res.json())
      .then((data) => {
        this.title = data.title;
        this.details = data.details;
      })
      .catch((err) => console.log(err));
  },
  methods:{
    handleSubmit(){
        let p = {
            title: this.title,details: this.details
        }
        fetch(this.uri,{
            method: 'PATCH',
            headers : { 'Content-Type': 'application/json'},
            body: JSON.stringify(p) })
            .then(() =>{  this.$router.push('/') })
            .catch((err) => console.log(err))
       
    }
  }
};
</script>
