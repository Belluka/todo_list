<template>
	<div>
		<!---<h1>You have completed {{todos.filter(todo => {return todo.done === true}).length}} tasks</h1>-->
    	<h1 style="background-color: #fff; color: #808080;"  class="ui center aligned block header">You've completed {{todos.filter(todo => {return todo.done === true}).length}} of {{todos.filter(todo => {return todo}).length}} tasks
    	</h1>
		<todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo">	
		</todo>
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
				if(this.todos[todoIndex].done == false)
					this.todos[todoIndex].done = true;
				else
					this.todos[todoIndex].done = false;
			}
		}
	}
</script>

<style>

</style>