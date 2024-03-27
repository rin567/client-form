<template>
	<form class="client-form">
		<legend>Создание нового клиента</legend>
		<span>Основная информация</span>
		<div class="mainInfoContainer">
			<Input
				label="Фамилия*"
				type="text"
				v-model.trim="$v.lastName.$model"
				:inputError="$v.lastName.$error"
				:maxLength="$v.lastName.$params.maxLength.max"
			/>
			<div class="error" v-if="!$v.lastName.required && $v.lastName.$dirty">
				Обязательное поле
			</div>
			<div class="error" v-if="!$v.lastName.alpha">Используйте кириллицу</div>
			<Input
				label="Имя*"
				type="text"
				v-model.trim="$v.firstName.$model"
				:inputError="$v.firstName.$error"
			/>
			<div class="error" v-if="!$v.firstName.required && $v.firstName.$dirty">
				Обязательное поле
			</div>
			<Input
				label="Отчество"
				type="text"
				v-model.trim="$v.surName.$model"
				:inputError="$v.surName.$error"
			/>
			<Input label="Дата рождения*" type="date" v-model="birth" />
			<span>Пол</span>
			<Checkbox label="Женщина" name="female" />
			<Checkbox label="Мужчина" name="male" />
			<Input label="Номер телефона*" type="tel" v-model="phoneNumber" />
			<Checkbox label="Не отправлять СМС" name="sendSMS" v-model="sendSMS" />
			<span>{{ sendSMS }}</span>
			<Select :options="groups" label="Группа клиентов*" name="selectGroup" />
			<Select :options="doctors" label="Лечащий врач" name="selectDoctor" />
		</div>
		<span>Адрес</span>
		<div class="addrContainer">
			<Input label="Индекс" name="index" type="text" />
			<Input label="Страна" name="country" type="text" />
			<Input label="Область" name="region" type="text" />
			<Input label="Город*" name="city" type="text" />
			<Input label="Улица" name="street" type="text" />
			<Input label="Дом" name="building" type="text" />
		</div>
		<span>Паспортные данные</span>
		<div class="passInfoContainer">
			<Select
				class="passInfoItem"
				:options="id"
				name="identifier"
				label="Тип документа*"
			/>
			<Input label="Серия" name="passSeries" type="text" />
			<Input label="Номер" name="passNumber" type="text" />
			<Input label="Кем выдан" name="placeOfIssue" type="text" />
			<Input label="Дата выдачи*" name="dateOfIssue" type="date" />
		</div>
		<Button />
	</form>
</template>

<script lang="ts">
import Vue from 'vue'
import { helpers, maxLength, required } from 'vuelidate/lib/validators'
import Button from './UI/Button.vue'
import Checkbox from './UI/Checkbox.vue'
import Input from './UI/Input.vue'
import Select from './UI/Select.vue'
const alpha = helpers.regex('alpha', /^[а-яё]*$/i)
export default Vue.extend({
	name: 'Form',
	components: {
		Button,
		Input,
		Select,
		Checkbox,
	},
	data: function () {
		return {
			id: ['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
			groups: ['VIP', 'Проблемные', 'ОМС'],
			doctors: ['Иванов', 'Захаров', 'Чернышева'],
			female: false,
			male: false,
			firstName: null,
			lastName: null,
			surName: null,
			birth: null,
			phoneNumber: null,
			gender: null,
			selectGroup: null,
			selectDoctor: null,
			sendSMS: 'true',
			index: null,
			country: null,
			region: null,
			street: null,
			city: null,
			building: null,
			selectID: null,
			passSeries: null,
			passNumber: null,
			placeOfIssue: null,
			dateOfIssue: null,
		}
	},
	validations: {
		lastName: {
			required,
			alpha,
			maxLength: maxLength(20),
		},
		firstName: {
			required,
			alpha,
		},
		surName: {
			alpha,
		},
		birth: {},
		phoneNumber: {},
	},
})
</script>

<style lang="sass">
.client-form
  display: flex
  flex-flow: column wrap
  gap: 1rem
  max-width: 742px
  border-radius: 10px
  background-color: white
  box-sizing: border-box
  margin: 5%
  padding: 3%
  box-shadow: 0 0 20px 1px rgba(0, 0 ,0, 0.2)
.error
  color: red
  font-size: 0.8rem
legend
  font-size: 1.5rem
span
  font-size: 1rem
  color: rgb(5, 5, 215)
Button
  justify-self: center
</style>
