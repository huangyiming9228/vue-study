<template>
	<div id="app">
        <create-todo @create-todo="addTodo"></create-todo>
		<todo-list
            v-bind:todos="todos"
        ></todo-list>
	</div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from "./components/CreateTodo";

export default {
	name: 'App',
	components: {
        TodoList,
        CreateTodo
    },
    data() {
        return {
            todos: [
                {
                    title: 'Todo A',
                    project: 'Project A',
                    done: false
                },
                {
                    title: 'Todo B',
                    project: 'Project B',
                    done: false
                },
                {
                    title: 'Todo C',
                    project: 'Project C',
                    done: false
                }
            ]
        };
    },
    methods: {
        addTodo(todo) {
            this.todos.push(todo);
        }
    }
}
</script>

<style>
#app {
	font-family: 'Avenir', Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
