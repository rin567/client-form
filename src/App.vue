<template>
	<div id="app">
		<Form />
	</div>
</template>

<script lang="ts">
import Form from './components/Form.vue'
export default {
	name: 'App',
	components: {
		Form,
	},
}
</script>

<style lang="scss">
body {
	margin: 0;
}
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	background: linear-gradient(
		to bottom left,
		rgb(5, 5, 215),
		rgb(129, 232, 243)
	);
	height: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
}
</style>
