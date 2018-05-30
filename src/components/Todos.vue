<template>
    <ul class="list-group">
        <li class="list-group-item"
            v-bind:class="{'completed':todo.completed}"
            v-for="(todo,index) in todos">
            {{todo.title}}
            <button class="btn pull-right btn-xs"
                    v-bind:class="[todo.completed ? 'btn-danger' : 'btn-success']"
                    v-on:click="toggleCompletion(todo)"
            >{{todo.completed ? 'undo' : 'completed' }}
            </button>
            <button class="btn btn-warning pull-right btn-xs"
                    v-on:click="deleteTodo(index)"
            >Delete
            </button>
        </li>
    </ul>
</template>
<style>
    .completed{
        color: #4cae4c;
        text-decoration: line-through;
    }
</style>
<script>
    export default{
        props:['todos'],


        methods:{
            deleteTodo(index){
                this.todos.splice(index,1)
            },
            toggleCompletion(todo){
                todo.completed = ! todo.completed
            }
        }
    }
</script>