<template>
	<div class="radio-container">
		<label class="radio-label" :for="name">{{ label }}</label>
		<div class="options-container">
			<div
				:id="name"
				@input="updateValue"
				v-for="option in options"
				:key="option.code"
			>
				<input type="radio" :value="option.code" v-model="currentValue" />
				<label for="option.name">{{ option.name }}</label>
			</div>
		</div>
	</div>
</template>

<script lang="ts">
import Vue from 'vue'

interface Option {
	code: string
	name: string
}
export default Vue.extend({
	name: 'radio',
	data: function () {
		return {
			currentValue: null,
		}
	},
	methods: {
		updateValue(event: Event) {
			this.$emit('input', (event.target as HTMLInputElement).value)
		},
	},
	props: {
		name: String,
		label: String,
		options: {
			type: Array as () => Option[],
			required: true,
		},
	},
})
</script>

<style lang="sass">
.radio-label
  font-size: 0.8rem
.options-container
  display: flex
  gap: 0.7rem
  margin-top: 0.5rem
</style>
