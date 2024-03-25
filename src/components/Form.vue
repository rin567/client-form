<template>
	<div class="form-container">
		<form>
			<legend>Создание нового клиента</legend>
			<Main-info />
			<Addr-info />
			<Pass-info />
			<Button />
		</form>
	</div>
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
			gender: ['Мужской', 'Женский'],
			group: ['VIP', 'Проблемные', 'ОМС'],
			sendSMS: false,
			index: '',
			country: '',
			region: '',
			street: '',
			city: '',
			building: '',
			identifier: ['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
			passSeries: '',
			passNumber: '',
			placeOfIssue: '',
			dateOfIssue: '',
		}
	},
}
</script>

<style lang="sass">
.form-container
	height: 100vh
	display: flex
	align-items: center
	justify-content: center
form
	width: 500px
	height: 400px
	border-radius: 10px
	background-color: white
	box-sizing: border-box
	margin: 2%
	padding: 3%
	box-shadow: 0 0 20px 1px rgba(0, 0 ,0, 0.2)
legend
	color: gray
</style>
