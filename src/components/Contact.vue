<template>
    <div class="box">
        <h2 :class="this.isContacted ? 'doneContacting' : 'needToContact'">{{name || "Name not provided"}}</h2>
        <hr />
        <h4 v-if="email"> Email : {{email}}</h4>
        <h4 v-if="mobile">Mobile : {{mobile}}</h4>
        <span>
<!--
            <button v-if="!this.isContacted" @click="changeContactStatus">Contact Now</button>
            <button v-else @click="changeContactStatus">Remind to Contact Again</button>
-->
        <label>Contacted</label>
       <input type="checkbox" 
              :checked="this.isContacted"
              @change="changeContactStatus">
        </span>
        
    </div>
</template>

<script>
export default{
name: 'Contact',
props: {
    id: Number,
    name: String,
    email: String,
    mobile: String,
    contacted: Boolean
    },
data(){
    return {
      isContacted: this.contacted      
    }
    },
methods:{
        changeContactStatus: function(){
            this.isContacted = !this.isContacted;
        this.$emit('onChangeContactStatus', this.name)
        }
    }
}
    
</script>

<style scoped>
    .box{
        background-color: cyan;
        margin: 10px;
        padding: 10px;
        border-radius: 10%;
        width: 30%;
        height: 200px;
    }
    
    .doneContacting{
        color: green;
    }
    .needToContact{
        color: red;
    }
</style>