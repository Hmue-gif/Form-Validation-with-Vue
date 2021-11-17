<template>
   <form @submit.prevent="submit">
       <h3>Form Validation</h3>

       <label for="">First Name</label>
       <input type="text" required placeholder="Enter Your First Name" v-model="fname">

       <label for="">First Name</label>
       <input type="text" required placeholder="Enter Your Last Name" v-model="lname">

       <label for="">Email</label>
       <input type="email" required placeholder="Enter Your Email" v-model="email">

       <label for="">Password</label>
       <input type="password" required placeholder="Enter Your Password" v-model="pass">
       <div v-if="err" class="errControl">
           <span class="errorIcon">&#10071</span>
           <p> {{err}} </p>
       </div>

        <label for="">Role</label>
       <select name="" id="" v-model="role">
           <option value="developer">Web developer</option>
           <option value="designer">Web Designer</option>
       </select>


       <label for="">Message</label>
       <input type="text" placeholder="Enter Your First Name" v-model="message" @keyup.ctrl="run">

        <ul v-for="data in datas" :key="data">
            <li> 
                {{data}}
                <span class="icon" @click="deleteData(data)">&#x2718</span> 
            </li>
        </ul>

       <input type="checkbox" v-model="check">
       <p class="para">Do you agreed these terms and conditions</p>

       <div class="btn-control">
           <button class="btn">Submit</button>
       </div>
   </form>

   <div class="backend">
        <h2>backend Data</h2>
        <p>First Name - {{fname}} </p>
        <p>Last Name - {{lname}}  </p>
        <p>Email - {{email}}  </p>
        <p>Password - {{pass}}  </p>
        <p>Password - {{role}}  </p>
        <p>Message - {{message}}  </p>
        <p>Password - {{check}}  </p>
   </div>
</template>

<script>
export default {
    data(){
        return{
            fname : "",
            lname : "",
            email : "",
            pass : "",
            message : "",
            datas : [],
            err : "",
            role : "",
            check : false
        }
    },
    methods:{
        run(e){
            if(e.key === "," && this.message!=""){
                this.datas.push(this.message);
                this.message = ""
            }
        },
        deleteData(data){
            this.datas = this.datas.filter(el=>{
                console.log(el);
                return el!=data;
            })
        },
        submit(){
            // console.log("submit");
            if(this.pass.length<=8){
                this.err = "your password need more than 8 characters"
            }
        }
    }
}
</script>

<style>
    h3{
        text-align: center;
        color: #fff;
        opacity: 0.5;
        letter-spacing: 1.2px;
    }
    form{
        width: 480px;
        background: #73C8A9;  /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #373B44, #73C8A9);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #373B44, #73C8A9); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
        border-radius: 10px ;
        margin: 100px auto;
        padding: 20px;
    }
    label{
        display: inline-block;
        font-weight: bold;
        font-size: 1em;
        color: #fff;
        opacity: 0.5;
        letter-spacing: 1px;
        margin: 4px 0 5px 0;
    }
    input,select{
        display: block;
        width: 100%;
        padding: 10px;
        border: none;
        outline: none;
        background: #fff;
        opacity: 0.5;
        margin: 6px 0;
    }
    input[type="checkbox"]{
        display: inline-block;
        width: 28px;
        position: relative;
        bottom: 1.7px;
        left: -2px;
    }

    .para{
        display: inline-block;
        color: #fff;
        opacity: 0.5;
    }
    .btn-control{
        text-align: center;
        margin: 8px 0 0 0;
    }
    .btn{
        padding: 10px;
        width: 80px;
        background: #fff;
        opacity: 0.5;
        border: 0;
        outline: 0;
    }
     .backend {
        text-align: center;
        font-size: 1.2em;
        color: darkblue;
    }
    .backend p{
        text-align: center;
        font-size: 1em;
        color: darkblue;
        opacity: 0.5;
    }
    ul li{
        margin: 5px 16px;
        color: #fff;
        opacity: 0.5;
    }
    .icon{
        cursor: pointer;
        color: red;
    }
    .errorIcon{
        color: crimson;
        opacity: 0.5;
        margin: 0 6px;
    }
    .errControl p{
        display: inline-block;
        color: crimson;
        margin: 5px 0;
        opacity: 0.5;
    }
</style>