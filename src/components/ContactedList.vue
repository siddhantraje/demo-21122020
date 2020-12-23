<template>
<div>
    <h1>Contacted List</h1>
<ul v-for="name in namesList" :key="name">
    <li>{{name}}</li>
    </ul></div>
</template>

<script>
export default{
name: 'ContactedList',
props: {
    "selectedNames" : Array
    },
data(){
    return {
    namesList : this.selectedNames
    }
   
    },
methods:{
        
    }
}
    
</script>

<style scoped>
    
</style>