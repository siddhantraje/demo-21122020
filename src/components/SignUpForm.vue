<template>
    <div>
    <h2>Sign Up Form {{this.name}} {{this.email}} {{this.mobile}}</h2>
        <div>
            <form>
                <div class="form-group">
                    <label>Name</label>
                    <input type="text" class="form-control" placeholder="Enter Name" v-model="name">
                    <label>Email</label>
                    <input type="text" class="form-control" placeholder="Enter Email"  v-model="email">
                    <label>Mobile</label>
                    <input type="text" class="form-control" placeholder="Enter Mobile"  v-model="mobile">
                    <button type="button" @click="submit" class="btn btn-success">Submit</button>
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
            persons: []
        }
    },
    methods: {
        submit(e){
        e.preventDefault();
        console.log(this.name, this.mobile);
            let person = { name: this.name || 'Not Provided', email: this.email || 'Not Provided', mobile: this.mobile || 'Not Provided' }
            this.persons.push(person);
        this.resetForm();
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