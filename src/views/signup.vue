<template>
<div >
    <div class="bg-img">
        <div class="header1">
            <app-header></app-header>
        </div>
    </div>
    <br>
    <div class="jumbotron container">
        <h1><b>Sign Up</b></h1>
        <br>
        <form class="container">
        <b-form-input v-model="user.user_name" placeholder="Name" :type="'text'" :state="null" required></b-form-input>
        <br>    
        <b-form-input v-model="user.email" placeholder="E-Mail" :type="'email'" :state="null" required></b-form-input>
        <br>
        <b-form-input v-model="user.password" placeholder="Password" :type="'password'" :state="null" required ></b-form-input>
        <br>
        <b-form-input  placeholder="Confirm Password" :type="'password'" :state="null" required></b-form-input>
        <br>
        <b-form-input v-model="user.country" placeholder="Country" :type="'text'" :state="null" required></b-form-input>
        <br>  
        </form>
        <button class="btn btn-success" @click="submit"><i class="fa fa-user-plus" aria-hidden="true"></i> Sign-Up</button>
        <div class="alert alert-success" v-show="flag">Your are now Signed-up. Thank you for registering. <router-link to="/login">Login-here</router-link> here </div>
        <br><br>
    </div>
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <appfooter></appfooter>
</div>
</template>




<script>
import header from "../components/header";
import footer from "../components/footer";
import axios from "axios";
export default {
    components: {
        appHeader: header,
        appfooter: footer
    },
    data: function(){
        return {
          user:{  
            user_name: null,
            email: null,
            password: null,
            country: null,
            active:[]
            },
            flag: false,
        };
    },
    methods:{
        submit(){
            this.flag=!this.flag;
            axios.post("https://subman-f6e20.firebaseio.com/user.json",this.user);
        }
    }

}
</script>


<style scoped>
    .bg-img{
        background: url("../assets/background.png");
        min-height: 300px;
        background-position: center;
        background-repeat: no-repeat;
        background-size: cover;
        position: relative;
        box-shadow: 10px 10px 54px -6px rgba(0, 0, 0, 0.75);
    }
    .header1{
        background-color: rgba(150, 152, 153,0.3);
    }

.jumbotron{
	background: rgba(0, 0, 0, 0.75);
    width: 35%;
    height: 50%;
    margin-top: 3%;
    color: white;
}
.jumbotron button{
    float: right;
}

@media (max-width: 900px){
    .jumbotron{
        width: 50%;
    }
}
@media (max-width: 400px){
    .jumbotron{
        width: 70%;
    }
}

</style>