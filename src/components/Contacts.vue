<template>
    <div class="container">
        <div class="row">
            <Contact  v-for="contact in contacts" class="col-lg-4"
                     :key=contact.id 
                     :id=contact.id 
                     :name="contact.name" 
                     :email="contact.email" 
                     :mobile="contact.mobile" 
                     :contacted="contact.contacted"
                     @onChangeContactStatus="displaySelectedName"
                     />
          </div>
      <ContactedList class="col-lg-4" :selectedNames="selectedNames"/>
  </div>
</template>

<script>
import Contact from './Contact.vue';
import ContactedList from './ContactedList.vue';
import { CONTACTS_INFO } from './sharedData/contactsInfo.js'

export default {
  name: 'Contacts',
  data(){
      return {
          selectedNames: [] ,
          contacts: CONTACTS_INFO
          
      }
  },
  methods: {  
      displaySelectedName:function(name){
          this.selectedName = name || 'Name not Provided'
          this.selectedNames.push(this.selectedName);
      } 
  },
  components: {
    Contact,
    ContactedList
  }
  
}
</script>

<style scoped>
  
</style>
