<script setup>


import {ref} from "vue"

const newTodo = ref ("")
const todos = ref([])

   function toggleDone(todo){
            todo.completed = !todo.completed
        }

        function removeTodo(index){
            todos.value.splice(index,1)
        }
        function markAllDone(){
            todos.value.forEach((todo)=> todo.completed =true)
        }
function addNewTodo(){
    todos.value.push({
        id: Date.now(),
        completed: false, 
        content: newTodo.value,
        });

        newTodo.value="";

      
         
    return {
    addNewTodo,
    newTodo,
    todos,
    toggleDone,
    markAllDone
}
}


</script>

<template>
<h1>Vue your todo</h1>
<form @submit.prevent="addNewTodo"> 
    <label> New Todo</label>
    <input v-model="newTodo" name="newTodo"> 
    <button>Add </button>
</form>
<button @click="markAllDone"> Mark All Done</button>
<ul>

<li v-for="(todo,index) in todos" :key="todo.id" class="todo">
    <h3 :class="{completed: todo.completed}" @click="toggleDone(todo)"> {{todo.content}}</h3>
    <button @click="removeTodo(index)"> Remove Todo</button>
     </li>
     </ul>

</template>

<style>
.todo{
    cursor: pointer;
}
.completed {
    text-decoration:line-through; 
    
}
</style>
