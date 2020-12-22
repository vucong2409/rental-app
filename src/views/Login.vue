<template>
  <div id="login d-flex align-items-center" >
    <div class="jumbotron rounded mx-auto d-block col-9">
      <div class="container d-flex justify-items-center"> 
       <div class="d-flex flex-column w-100">
         <div class="mx-auto">
           <b class="brand"> LOGIN </b>
         </div>

         <div class="mx-auto mb-4">
           <input type="text" class="form-control" v-model="username"  />
         </div>

         <div class="mx-auto mb-4">
           <input type="password" class="form-control" v-model="password" />
         </div>
         <div class="mx-auto mb-4">
           <button type="button" class="btn btn-info" @click="sendAPI()">Submit</button>
         </div>
         <div class="mx-auto mb-4">
           {{check_status}}
         </div>
        </div>
      </div>
     </div>
  </div>
</template>

<script>
import axios from "axios"
  export default {
    name : 'login',
    components: {
    }, 
    props : {
      check_status : String,
      username : String,
      password : String 
    },
    data() {
      return {
      }
    },
     
    methods : {
      sendAPI() {
        const user = {
          "username" : this.username,
          "password" : this.password
        }
        axios.post("http://localhost:8081/api/user/sign-in", user) 
             .then(res => {
               this.check_status = res.data;
             })
             .catch(err => {
               console.log(err)
             })
      }
    }
    
    
  }   
  
</script>

<style>
.brand {
  font-size: 30px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>
