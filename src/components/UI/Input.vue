<template>
	<div class="input-container">
		<label class="input-label" :for="name">{{ label }}</label>
		<input
			class="input"
			:type="type"
			:id="name"
			:value="value"
			@input="onInput"
		/>
	</div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
	name: 'Input',
	props: {
		name: String,
		label: String,
		type: String,
		value: String,
	},
	methods: {
		onInput(event: Event) {
			this.$emit('input', (event.target as HTMLInputElement).value)
		},
	},
})
</script>

<style lang="sass">
.input-label
  font-size: 0.8rem
  margin-bottom: 0.25rem
  display: block
.input
  display: block
  height: calc(1rem + 2px)
  padding: 0.375rem 0.75rem
  font-family: inherit
  font-size: 1rem
  font-weight: 400
  line-height: 1.5
  color: #212529
  background-color: #fff
  background-clip: padding-box
  border: 1px solid #bdbdbd
  border-radius: 0.25rem
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out
  &:focus
    color: #212529
    background-color: #fff
    border-color: #bdbdbd
    outline: 0
    box-shadow: 0 0 0 0.2rem rgba(158, 158, 158, 0.25)
</style>
