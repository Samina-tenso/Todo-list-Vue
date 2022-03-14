<script setup>
import {ref} from "vue"
const newTodo = ref ("")
function addNewTodo(){
    console.log("form was submitted")
    return {
    addNewTodo,
    newTodo,
}
}

</script>

<template>
<h1>Vue your todo</h1>
<form @submit.prevent="addNewTodo"> 
    <label> New Todo</label>
    <input v-model="newTodo" name="new-todo"> 
    <button>Add </button>
</form>

</template>

<style>

</style>
