<template>
  <div id="app"> 
    <todo-header></todo-header>
    <todo-input v-on:add="addTodoItem" ></todo-input>
    <!-- remove 버튼 구현 -->
    <todo-list 
      v-bind:items="todoItems"
      @removeItem="removeItem"
    >
    </todo-list>
    <todo-footer v-on:clear="clearTodoItems"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';
// vim
export default {
	components: {
		// 'todo-header': TodoHeader,
		// 'todo-input': TodoInput,
		// 'todo-list': TodoList,
		// 'todo-footer': TodoFooter,
		TodoHeader,
		TodoInput,
		TodoList,
		TodoFooter,
	},
	data() {
		return {
			todoItems: [],
		};
	},
	methods: {
		removeItem: function(todoItem, index) {
			localStorage.removeItem(todoItem);
			this.todoItems.splice(index, 1);
		},
		addTodoItem: function(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		clearTodoItems: function() {
			this.todoItems = [];
			localStorage.clear();
		},
		fetchTodoItems: function() {
			for (var i = 0; i < localStorage.length; i++) {
				var item = localStorage.key(i);
				this.todoItems.push(item);
			}
		},
	},
	created() {
		// console.log('생성되었음');
		this.fetchTodoItems();
	},
};
</script>

<style scoped>
</style>