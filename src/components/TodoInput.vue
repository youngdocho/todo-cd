<template>
  <div>
    <input 
    type="text" 
    v-model="inputText"
    v-on:keyup.enter="addTodo"
    >
    <button v-on:click="addTodo">add</button> 
  </div>
</template>

<script>
export default {
	data: function() {
		return {
			inputText: '',
		};
	},
	methods: {
		addTodo: function() {
			var value = this.inputText;
			// localStorage.setItem(value, value);
			this.$emit('add', value);
			this.clearInput();
		},
		clearInput: function() {
			this.inputText = '';
		},
	},
};
</script>
