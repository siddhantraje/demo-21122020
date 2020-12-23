<template>
    <div>
    <h2>Sign Up Form {{this.name}} {{this.email}} {{this.mobile}}</h2>
        <div>
            <form>
                <div class="form-group">
                    <label>Name</label>
                    <input type="text" class="form-control" placeholder="Enter Name" v-model="name">
                    <span class="text-danger" v-if="errors.name">{{errors.name}}</span>
                    <br>
                    <label>Email</label>
                    <input type="text" class="form-control" placeholder="Enter Email"  v-model="email">
                    <span class="text-danger" v-if="errors.email">{{errors.email}}</span>
                    <br>
                    <label>Mobile</label>
                    <input type="text" class="form-control" placeholder="Enter Mobile"  v-model="mobile">
                    <span class="text-danger" v-if="errors.mobile">{{errors.mobile}}</span>
                    <br>
                    <button type="button" @click="validateForm" class="btn btn-success">Submit</button>
                </div>                
            </form>
        </div>
        
    <h2> People SignedUp Till Now</h2>
        <table width="100%">
            <th>Name</th>
            <th>Email</th>
            <th>Mobile</th>
            <tr v-for="person in persons" :key='person.name'>
                <td :style="{color: person.name==='Not Provided' ? 'red' : '' }">{{person.name}}</td>
                <td :style="{color: person.email==='Not Provided' ? 'red' : '' }">{{person.email}}</td>
                <td :style="{color: person.mobile==='Not Provided' ? 'red' : '' }">{{person.mobile}}</td>
            </tr>
        </table>
        </div>
</template>

<script>
export default{
name: 'SignUpForm',
    data(){
        return {
            name: '',
            email: '',
            mobile: '',
            persons: [],
            errors: {
                name: '',
                email: '',
                mobile: '',
            }
        }
    },
    methods: {
        submitForm(){
            let person = { name: this.name.trim(), email: this.email, mobile: this.mobile }
            this.persons.push(person);
        this.resetForm();
    },
        validateForm(e){
            let emailRegEx = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
            let mobileRegEx = /^[789]\d{9}$/
            e.preventDefault();
            this.errors = {
                name: '',
                email: '',
                mobile: '',
            }
            if(this.name.trim().length === 0){
                this.errors.name="Name is required";
            }
            if(!this.email){
                this.errors.email="Email is required";
            }
            if(!this.mobile){
                this.errors.mobile="Mobile is required";
            }
            if(this.email && !emailRegEx.test(this.email)){
                this.errors.email="Enter Valid Email"
            }
            if(this.mobile && !mobileRegEx.test(this.mobile)){
                this.errors.mobile="Enter 10 digit Valid Mobile Number"
            }
            if(!this.errors.name && !this.errors.email && !this.errors.mobile){
                if(confirm("Do you want to submit the Data ?"))
                this.submitForm();                    
            }
        },
        resetForm(){
                this.name = '';
                this.email = '';
                this.mobile = '';
            }
}

}
    
</script>

<style scoped>
    table, th, td {
  border: 1px solid black;
}
</style>