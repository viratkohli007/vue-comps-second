<template>
    <div class="component">
        <h3>You may edit the User here</h3>
        <p>Edit me!</p>
        <p>Age is {{ userAge }}</p>
        <button @click="editAge">edit Age</button>
    </div>
</template>

<script>
import { eventBus } from '../main'
export default{
    props:{
        userAge:{
            type: Number
        }
    },
    methods:{
        editAge(){
            this.userAge = 25
            // this.$emit('ageWasReset', this.userAge)
            eventBus.$emit('ageWasReset', this.userAge)
        }
    }
}
</script>

<style scoped>
    div {
        background-color: lightgreen;
    }
</style>
