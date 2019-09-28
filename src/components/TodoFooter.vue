<template>
  <div>
    <!-- <button v-on:click="removeAll">clear all</button> -->
    <button @click="clearnAllItems">clear all</button>
  </div>
</template>

<script>
export default {
	methods: {
		clearnAllItems: function() {
			// 화면의 리스트는 어떻게 지울까?
			localStorage.clear();
			this.$emit('clear');
		},
	},
};
</script>

<style scoped>
</style>