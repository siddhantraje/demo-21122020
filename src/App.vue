
<template>
  <div id="app" class="container">
    <Contacts />
    <SignUpForm />
  </div>
</template>

<script>
import Contacts from './components/Contacts.vue';
import SignUpForm from './components/SignUpForm'

export default {
  name: 'App',
  data(){
      return {
          val: "Hello",
          nameOfClass: "yellowText",
      }
  },
  methods: {  
  },
  components: {
    Contacts,
    SignUpForm
  }
  
}
</script>

<style scoped>

</style>
