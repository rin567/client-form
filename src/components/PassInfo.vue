<template>
	<div class="passInfoContainer">
		<Select
			class="passInfoItem"
			:options="identifier"
			name="identifier"
			label="Тип документа"
		/>
		<div class="passInfoItem">
			<Input label="Серия" name="passSeries" />
			<Input label="Номер" name="passNumber" />
		</div>
		<div class="passInfoItem">
			<Input label="Кем выдан" name="placeOfIssue" />
			<Input label="Дата выдачи" name="dateOfIssue" />
		</div>
	</div>
</template>

<script lang="ts">
import Vue from 'vue'
import Input from './UI/Input.vue'
import Select from './UI/Select.vue'
export default Vue.extend({
	data: function () {
		return {
			identifier: ['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
		}
	},
	components: {
		Input,
		Select,
	},
})
</script>

<style lang="sass">
.passInfoContainer
  display: flex
  flex-wrap: wrap
  gap: 0.5rem
.passInfoItem
  display: flex
  flex-wrap: wrap
  gap: 0.5rem
</style>
