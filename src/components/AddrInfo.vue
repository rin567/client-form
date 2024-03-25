<template>
	<div class="addrContainer">
		<Input label="Индекс" name="index" />
		<Input label="Страна" name="country" />
		<Input label="Область" name="region" />
		<Input label="Город" name="city" />
		<Input label="Улица" name="street" />
		<Input label="Дом" name="building" />
	</div>
</template>

<script lang="ts">
import Vue from 'vue'
import Input from './UI/Input.vue'
export default Vue.extend({
	components: {
		Input,
	},
})
</script>

<style lang="sass">
.addrContainer
  display: flex
  flex-wrap: wrap
  gap: 0.5rem
</style>
