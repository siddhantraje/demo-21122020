
<template>
  <div>
        <Contact v-for="contact in contacts" 
                 :key=contact.id 
                 :id=contact.id 
                 :name="contact.name" 
                 :email="contact.email" 
                 :mobile="contact.mobile" 
                 :contacted="contact.contacted"
                 @onChangeContactStatus="displaySelectedName"
                 />
      <hr />
      <h3>Selected Name : {{selectedName || 'Nothing Selected'}}</h3>
  </div>
</template>

<script>
import Contact from './Contact.vue'

export default {
  name: 'Contacts',
  data(){
      return {
          selectedName: '',
          contacts: [
            {
                id: 101,
                name: "Siddhant",
                email: "siddhant@gmail.com",
                mobile: "999999999",
                contacted: true
            },
            {
                id: 102,
                name: "Sachin",
                contacted: false
            },
            {
                id: 103,
                name: "Bismay",
                mobile: "1111111111",
                contacted: false
            },
            {
                id: 104,
                email: "anadi@gmail.com",
                contacted: false
            },
          ]
      }
  },
  methods: {  
      displaySelectedName:function(name){
          console.log(name);
          this.selectedName = name
      } 
  },
  components: {
    Contact
  }
  
}
</script>

<style scoped>
  
</style>
