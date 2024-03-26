<template>
	<div class="select-container">
		<label class="select-label" :for="name">{{ label }}</label>
		<select class="select" :id="name" v-model="currentValue">
			<option v-for="(option, index) in options" :key="index">
				{{ option }}
			</option>
		</select>
	</div>
</template>

<script lang="ts">
export default {
	name: 'Select',
	data: function () {
		return {
			currentValue: null,
		}
	},
	props: {
		name: String,
		label: String,
		options: Array,
	},
}
</script>

<style lang="sass">
.select-label
  margin-bottom: 0.25rem
  display: block
  font-size: 0.8rem
.select
  display: block
  height: calc(1.85rem + 2px)
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
</style>
