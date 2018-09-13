<template>
    <div>
        <p>已完成的项目数：{{ todos.filter(item => {return item.done === true}).length }}</p>
        <p>未完成的项目数：{{ todos.filter(item => {return item.done === false}).length }}</p>
        <todo 
            v-for="(todo, index) in todos" 
            :key="index" 
            :todo.sync="todo"
            @delete-todo="deleteTodo"
            @complete-todo="completeTodo"
        ></todo>
    </div>
</template>

<script>
import Todo from './Todo';
export default {
    props: ['todos'],
    components: {
        Todo
    },
    methods: {
        deleteTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
        },
        completeTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos[todoIndex].done = true;
            console.log(this.todos);
        }
    }
}
</script>

<style>

</style>