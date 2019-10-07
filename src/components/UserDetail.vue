<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>user name is {{ name }}</p>
        <P>USER age is {{ userAge }}</P>
        <button @click="changeName">change name</button>
        <button @click="resetFn">change name cb</button>
    </div>
</template>

<script>
import { eventBus } from '../main'
    export default{
        props:{
            name:{
                type : String
            },
            resetFn:{
                type : Function
            },
            userAge:{
                type: Number
            }
        },
        methods:{
            changeName(){
                this.name = 'Max'
                this.$emit('nameWasReset', this.name)
            }
        },
        created(){
            eventBus.$on('ageWasReset', (age)=>{
                this.userAge = age
            })
        }
    }
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
