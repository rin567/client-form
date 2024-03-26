<template>
	<div class="checkbox-container">
		<input type="checkbox" class="checkbox-checkbox" :name="name" :id="name" />
		<label class="checkbox-label" :for="name">{{ label }}</label>
	</div>
</template>

<script lang="ts">
export default {
	name: 'Checkbox',
	props: {
		name: String,
		label: String,
		value: String,
	},
}
</script>

<style lang="sass">
.checkbox-label
  font-size: 1rem
</style>
