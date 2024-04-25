 <template>
    <img class="logo" src="../assets/logo.png">
    <h1>Sing Up</h1>
    <div class="register">

        <input type="text" v-model="name" placeholder="Enter Name">
        <input type="email" v-model="email" placeholder="Enter Email">
        <input type="password" v-model="password" placeholder="Enter Password">
        <button @click="signUp" type="submit">Sign Up</button>


    </div>
 </template>
 <script>
import axios from 'axios';

export default {
    name:'SingUp',
    data(){

        return{
            name:'',
            email:'',
            password:''
        }
    },

    methods:{
     
        async signUp(){
            let result = await axios.post("http://localhost:3000/users",{
            name:this.name,
            email:this.email,
            password:this.password
            });
            console.log(result);
            if(result.status==201){
                alert("SignUp done");
                localStorage.setItem("user-info",JSON.stringify(result.data));
            }
        }

    }
}
</script>

<style>

.logo{
width:500px;
}
.register input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom:30px ;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid orange;
}
.register button{

    width: 320px;
    height: 40px;
    border: 1px solid orange;
    background:orange ;
    color: white;
    cursor: pointer;
}
.register{
    margin-bottom: 150px;
}

</style>