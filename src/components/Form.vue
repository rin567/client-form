<template>
	<form>
		<legend>Создание нового клиента</legend>
		<span>Основная информация</span>
		<Main-info />
		<span>Адрес</span>
		<Addr-info />
		<span>Паспортные данные</span>
		<Pass-info />
		<Button />
	</form>
</template>

<script lang="ts">
import AddrInfo from './AddrInfo.vue'
import MainInfo from './MainInfo.vue'
import PassInfo from './PassInfo.vue'
import Button from './UI/Button.vue'

export default {
	name: 'Form',
	components: {
		MainInfo,
		AddrInfo,
		PassInfo,
		Button,
	},
	data: function () {
		return {
			firstName: '',
			lastName: '',
			surName: '',
			birth: '',
			phoneNumber: '',
			gender: '',
			selectGroup: '',
			doctor: '',
			sendSMS: false,
			index: '',
			country: '',
			region: '',
			street: '',
			city: '',
			building: '',
			identifier: '',
			passSeries: '',
			passNumber: '',
			placeOfIssue: '',
			dateOfIssue: '',
		}
	},
}
</script>

<style lang="sass">
form
  display: flex
  flex-flow: column wrap
  gap: 1rem
  flex: min-content
  max-width: 800px
  border-radius: 10px
  background-color: white
  box-sizing: border-box
  margin: 2%
  padding: 3%
  box-shadow: 0 0 20px 1px rgba(0, 0 ,0, 0.2)
legend
  font-size: 1.5rem
span
  font-size: 1rem
  color: rgb(5, 5, 215)
</style>
