<template>
    <!-- submit collet all data from form -->
    <!-- @submit.prevent => prevent => not refresh browser -->
    <form @submit.prevent="submit">
        <!-- v-modal trace the user input for email  -->
        <label for="email">Email</label>
        <input type="email" required v-model="email">

        <label for="password">Password</label>
        <input type="password" required v-model="password">
        <p v-if="errMsg" class="error">{{ errMsg }}</p>

        <label for="">Role</label>
        <select v-model="role">
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>

        <div>
            <label for="">Skill</label>
            <input type="text" @keyup.ctrl="addSkill" v-model="skill" >
        </div>

        <!-- :key = "skill" => unique key => for optional when skill is obj  :key shoudl be id :key = "id" boz id is unique-->
        <div v-for="skill in skills" :key="skill">
            {{ skill }} <span class="cross" @click="delSkill(skill)"> &#10006; </span>
        </div>
        
        <div>
            <!-- checkbox select is like other but use bool -->
            <input type="checkbox" v-model="accept">
            <label for="">Accept Terms and condition</label>
        </div>

        <!-- for test multi check box  -->
        <!-- value store data -->
        <!-- <label for="">Check Name</label><br/>
        <div>
            <input type="checkbox" value="MinKhant" v-model="names">
            <label>Min Khant</label>
        </div>
        <div>
            <input type="checkbox" value="AungTunKyaw" v-model="names">
            <label>Aung Tun Kyaw</label>
        </div>
        <div>
            <input type="checkbox" value="AungPhyoPaing" v-model="names">
            <label>Aung Phyo Paing</label>
        </div> -->
        
        <div class="align">
            <button class="create">Create Account</button>
        </div>

    </form>
</template>

<script>
    export default {
        data(){
            return{
                // can write email : "minkhant" => default
                email : "",
                password : "",
                role : "",
                accept: false,
                // names : [],
                skill : "",
                skills : [],
                errMsg : "",
            }
        },
        methods :{
            addSkill(event){
                if (event.key === "," && this.skill){
                    this.skills.push(this.skill);
                    this.skill = "";
                }
            },
            delSkill(skill){
                this.skills = this.skills.filter(loop_skill =>{
                    return loop_skill != skill;
                })
            },
            submit(){
                if (this.password.length < 8){
                    this.errMsg = "Password must be at least 8 character";
                }
            }
        }
    }
</script>


<style scoped>

form{
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label{
    color: #aaa;
    display: inline-block;
    margin: 25px 0px 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input,
select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.cross{
    cursor: pointer;
    color: red;
}

.create{
    background: royalblue;
    padding: 8px;
    color: white;
    border-radius: 10px;
}

.align{
    text-align: center;
}
.error{
    color: red;
}
</style>