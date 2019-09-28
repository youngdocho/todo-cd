<template>
  <div>
    <!-- <button v-on:click="fetchTodoItems">get all</button> -->
    <ul>
      <li 
      v-for="(todoItem, index) in items"
      v-bind:key="index"
      >
        {{ todoItem }}
        <button v-on:click="removeTodoItem(todoItem, index)">remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
	// 인스턴스 옵션 속성
	// data() {
	// 	return {
	// 		todoItems: [],
	// 	};
	// },
	props: ['items'],
	methods: {
		// fetchTodoItems: function() {
		// 	for (var i = 0; i < localStorage.length; i++) {
		// 		var item = localStorage.key(i);
		// 		this.todoItems.push(item);
		// 	}
		// },
		removeTodoItem: function(todoItem, index) {
			// this.todoItems.splice(index, 1);

			this.$emit('removeItem', todoItem, index);
		},
	},
	// created() {
	// 	// console.log('생성되었음');
	// 	this.fetchTodoItems();
	// },
};
</script>

<style scoped>
</style>