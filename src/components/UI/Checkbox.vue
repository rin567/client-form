<template>
	<div class="checkbox-container">
		<input
			type="checkbox"
			class="checkbox-checkbox"
			:name="name"
			:id="name"
			v-model="checked"
			@change="updateValue"
		/>
		<label class="checkbox-label" :for="name">{{ label }}</label>
	</div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
	name: 'Checkbox',
	props: {
		name: String,
		label: String,
	},
	data: function () {
		return {
			checked: false,
		}
	},
	methods: {
		updateValue() {
			this.$emit('input', !this.checked)
		},
	},
})
</script>

<style lang="sass">
.checkbox-label
  font-size: 1rem
.checkbox-container
  display: flex
  align-items: center
  padding-top: 1rem
</style>
