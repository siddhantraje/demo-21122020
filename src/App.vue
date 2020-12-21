
<template>
  <div id="app">
    <Contacts />
  </div>
</template>

<script>
import Contacts from './components/Contacts.vue'

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
    Contacts
  }
  
}
</script>

<style scoped>

</style>
