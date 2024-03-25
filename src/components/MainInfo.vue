<template>
	<div class="mainInfoContainer">
		<div class="mainInfoItem">
			<Input label="Фамилия" />
			<Input label="Имя" />
			<Input label="Отчество" />
			<Input label="Дата рождения" />
			<Input label="Номер телефона" />
			<Checkbox class="padding" label="Не отправлять СМС" name="sendSMS" />
		</div>
		<span>Пол</span>
		<div class="mainInfoItem">
			<Checkbox label="Женщина" name="female" />
			<Checkbox label="Мужчина" name="male" />
		</div>
		<div class="mainInfoItem">
			<Select :options="group" label="Группа клиентов" name="selectGroup" />
			<Select :options="doctor" label="Лечащий врач" name="selectDoctor" />
		</div>
	</div>
</template>

<script lang="ts">
import Vue from 'vue'
import Checkbox from './UI/Checkbox.vue'
import Input from './UI/Input.vue'
import Select from './UI/Select.vue'
export default Vue.extend({
	data: function () {
		return {
			group: ['VIP', 'Проблемные', 'ОМС'],
			doctor: ['Иванов', 'Захаров', 'Чернышева'],
		}
	},
	components: {
		Input,
		Select,
		Checkbox,
	},
})
</script>

<style lang="sass">
.mainInfoContainer
  display: flex
  flex-wrap: wrap
  gap: 0.5rem
  span
    font-size: 0.8rem
    color: black
.mainInfoItem
  width:100%
  display: flex
  flex-wrap: wrap
  gap: 0.5rem
  align-items: center
  .padding
    box-sizing: border-box
    padding-top: 1rem
</style>
