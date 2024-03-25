<template>
	<div class="input-text-container">
		<label class="input-text-label" for="first-name">Имя</label>
		<input
			class="input-text-input"
			type="text"
			name="first-name"
			id="first-name"
		/>
	</div>
</template>

<script lang="ts">
export default {
	name: 'Input',
	props: [],
}
</script>

<style lang="sass">
.input-text-container
	margin-bottom: 1 rem

.input-text-label
	display: block
	color: gray
	margin-bottom: 0.25rem
.input-text-input
	display: block
	height: calc(2.25rem + 2px)
	width: 100%
	padding: 0.375rem
</style>
