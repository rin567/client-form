<template>
	<form class="client-form" @submit.prevent="onSubmit">
		<legend>Создание нового клиента</legend>
		<span>Основная информация</span>
		<div class="form-section">
			<div class="form-section-item">
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
			</div>
			<div class="form-section-item">
				<Input
					label="Имя*"
					type="text"
					v-model.trim="$v.firstName.$model"
					:inputError="$v.firstName.$error"
					:maxLength="$v.firstName.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.firstName.required && $v.firstName.$dirty">
					Обязательное поле
				</div>
				<div class="error" v-if="!$v.firstName.alpha">
					Используйте кириллицу
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Отчество"
					type="text"
					v-model.trim="$v.surName.$model"
					:inputError="$v.surName.$error"
					:maxLength="$v.surName.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.surName.alpha">Используйте кириллицу</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Дата рождения*"
					type="date"
					v-model.trim="$v.birth.$model"
					:inputError="$v.phoneNumber.$error"
				/>
				<div class="error" v-if="!$v.birth.required && $v.birth.$dirty">
					Обязательное поле
				</div>
			</div>
			<Radio :options="genders" label="Пол" v-model="gender" />
			<div class="form-section-item">
				<Input
					label="Номер телефона*"
					type="tel"
					v-model="phoneNumber"
					:inputError="$v.phoneNumber.$error"
					:maxLength="$v.phoneNumber.$params.maxLength.max"
					:width="100"
				/>
				<div class="error" v-if="!$v.phoneNumber.phoneNum">
					Введите номер в формате: 79123456789
				</div>
				<div
					class="error"
					v-if="!$v.phoneNumber.required && $v.phoneNumber.$dirty"
				>
					Обязательное поле
				</div>
			</div>
			<Checkbox label="Не отправлять СМС" name="sendSMS" v-model="sendSMS" />
			<div class="form-section-item">
				<Multiselect
					:options="groups"
					label="Группа клиентов*"
					name="selectGroup"
					v-model="selectGroup"
					:selectError="submitStatus == 'ERROR' && !selectGroup"
				/>
				<div class="error" v-if="submitStatus == 'ERROR' && !selectGroup">
					Обязательное поле
				</div>
			</div>
			<Select
				:options="doctors"
				label="Лечащий врач"
				name="selectDoctor"
				v-model="selectDoctor"
			/>
		</div>
		<span>Адрес</span>
		<div class="form-section">
			<div class="form-section-item">
				<Input
					label="Индекс"
					name="index"
					type="text"
					v-model.trim="$v.index.$model"
					:inputError="$v.index.$error"
					:maxLength="$v.index.$params.maxLength.max"
					:width="55"
				/>
				<div class="error" v-if="!$v.index.minLength && $v.index.numeric">
					Минимальная длина {{ $v.index.$params.minLength.min }} символов
				</div>
				<div class="error" v-if="!$v.index.numeric">
					Используйте только цифры
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Страна"
					name="country"
					type="text"
					v-model.trim="$v.country.$model"
					:inputError="$v.country.$error"
					:maxLength="$v.country.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.country.alpha">Используйте кириллицу</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Область"
					name="region"
					type="text"
					v-model.trim="$v.region.$model"
					:inputError="$v.region.$error"
					:maxLength="$v.region.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.region.alpha">Используйте кириллицу</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Город*"
					name="city"
					type="text"
					v-model.trim="$v.city.$model"
					:inputError="$v.city.$error"
					:maxLength="$v.city.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.city.required && $v.city.$dirty">
					Обязательное поле
				</div>
				<div class="error" v-if="!$v.city.alpha">Используйте кириллицу</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Улица"
					name="street"
					type="text"
					v-model.trim="$v.street.$model"
					:inputError="$v.street.$error"
					:maxLength="$v.street.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.street.alphaNum">
					Используйте кириллицу
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Дом"
					name="building"
					type="text"
					v-model.trim="$v.building.$model"
					:inputError="$v.building.$error"
					:maxLength="$v.building.$params.maxLength.max"
					:width="38"
				/>
				<div class="error" v-if="!$v.building.numeric">
					Используйте только цифры
				</div>
			</div>
		</div>
		<span>Паспортные данные</span>
		<div class="form-section">
			<div class="form-section-item">
				<Select
					class="passInfoItem"
					:options="id"
					name="identifier"
					label="Тип документа*"
					v-model="selectID"
					:selectError="submitStatus == 'ERROR' && !selectID"
				/>
				<div class="error" v-if="submitStatus == 'ERROR' && !selectID">
					Обязательное поле
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Серия"
					name="passSeries"
					type="text"
					:width="38"
					v-model.trim="$v.passSeries.$model"
					:inputError="$v.passSeries.$error"
					:maxLength="$v.passSeries.$params.maxLength.max"
				/>
				<div
					class="error"
					v-if="!$v.passSeries.minLength && $v.passSeries.numeric"
				>
					Минимальная длина {{ $v.passSeries.$params.minLength.min }} символа
				</div>
				<div class="error" v-if="!$v.passSeries.numeric">
					Используйте только цифры
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Номер"
					name="passNumber"
					type="text"
					v-model.trim="$v.passNumber.$model"
					:inputError="$v.passNumber.$error"
					:maxLength="$v.passNumber.$params.maxLength.max"
					:width="55"
				/>
				<div
					class="error"
					v-if="!$v.passNumber.minLength && $v.passNumber.numeric"
				>
					Минимальная длина {{ $v.passNumber.$params.minLength.min }} символов
				</div>
				<div class="error" v-if="!$v.passNumber.numeric">
					Используйте только цифры
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Дата выдачи*"
					name="dateOfIssue"
					type="date"
					v-model.trim="$v.dateOfIssue.$model"
					:inputError="$v.dateOfIssue.$error"
				/>
				<div
					class="error"
					v-if="!$v.dateOfIssue.required && $v.dateOfIssue.$dirty"
				>
					Обязательное поле
				</div>
			</div>
			<div class="form-section-item">
				<Input
					label="Кем выдан"
					name="placeOfIssue"
					type="text"
					v-model.trim="$v.placeOfIssue.$model"
					:inputError="$v.placeOfIssue.$error"
					:maxLength="$v.placeOfIssue.$params.maxLength.max"
				/>
				<div class="error" v-if="!$v.placeOfIssue.alphaNum">
					Используйте кириллицу
				</div>
			</div>
		</div>
		<Button />
		<ModalWindow v-if="submitStatus === 'OK'" v-model="submitStatus" />
	</form>
</template>

<script lang="ts">
import Vue from 'vue'
import {
	helpers,
	maxLength,
	minLength,
	numeric,
	required,
} from 'vuelidate/lib/validators'
import ModalWindow from './ModalWindow.vue'
import Button from './UI/Button.vue'
import Checkbox from './UI/Checkbox.vue'
import Input from './UI/Input.vue'
import Multiselect from './UI/Multiselect.vue'
import Radio from './UI/Radio.vue'
import Select from './UI/Select.vue'
const alpha = helpers.regex('alpha', /^[а-яё-]*$/i)
const alphaNum = helpers.regex('alphaNum', /^[а-яё0-9-№\s]*$/i)
const phoneNum = helpers.regex('phoneNum', /^([7]{1}[0-9]{10})*$/i)
export default Vue.extend({
	name: 'Form',
	components: {
		Button,
		Input,
		Select,
		Checkbox,
		Radio,
		Multiselect,
		ModalWindow,
	},
	data: function () {
		return {
			id: ['Паспорт', 'Свидетельство о рождении', 'Вод. удостоверение'],
			groups: ['VIP', 'Проблемные', 'ОМС'],
			doctors: ['Иванов', 'Захаров', 'Чернышева'],
			genders: [
				{
					code: 'male',
					name: 'Мужской',
				},
				{
					code: 'female',
					name: 'Женский',
				},
			],
			submitStatus: '',
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
			maxLength: maxLength(25),
		},
		firstName: {
			required,
			alpha,
			maxLength: maxLength(25),
		},
		surName: {
			alpha,
			maxLength: maxLength(25),
		},
		//dop
		birth: {
			required,
		},
		//dop
		phoneNumber: {
			required,
			phoneNum,
			maxLength: maxLength(11),
		},
		index: {
			minLength: minLength(6),
			maxLength: maxLength(6),
			numeric,
		},
		country: {
			alpha,
			maxLength: maxLength(25),
		},
		region: {
			alpha,
			maxLength: maxLength(25),
		},
		street: {
			alphaNum,
			maxLength: maxLength(25),
		},
		city: {
			required,
			alpha,
			maxLength: maxLength(25),
		},
		building: {
			numeric,
			maxLength: maxLength(25),
		},
		passSeries: {
			minLength: minLength(4),
			maxLength: maxLength(4),
			numeric,
		},
		passNumber: {
			maxLength: maxLength(6),
			minLength: minLength(6),
			numeric,
		},
		placeOfIssue: {
			alphaNum,
			maxLength: maxLength(100),
		},
		//dop
		dateOfIssue: {
			required,
		},
	},
	methods: {
		onSubmit() {
			if (!this.selectGroup && !this.selectID) {
				this.submitStatus = 'ERROR'
			}
			this.$v.$touch()
			if (this.$v.$invalid) {
				this.submitStatus = 'ERROR'
			} else {
				// submit logic here
				this.submitStatus = 'PENDING'
				setTimeout(() => {
					this.submitStatus = 'OK'
				}, 500)
			}
		},
	},
})
</script>

<style lang="sass">
.client-form
  display: flex
  flex-flow: column wrap
  gap: 1rem
  align-items: center
  border-radius: 10px
  background-color: white
  box-sizing: border-box
  margin: 5%
  padding: 3%
  box-shadow: 0 0 20px 1px rgba(0, 0 ,0, 0.2)
.form-section
  display: flex
  flex-flow: row wrap
  max-width: 700px
  gap: 1rem
.error
  color: red
  font-size: 0.8rem
legend
  font-size: 1.5rem
span
  font-size: 1rem
  color: rgb(5, 5, 215)
  align-self: flex-start
Button
  justify-self: center
</style>
