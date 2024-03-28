<template>
	<transition name="modal">
		<div class="modal-mask">
			<div class="modal-wrapper">
				<div class="modal-container">
					<div class="modal-body">
						<slot name="body"> Клиент создан! </slot>
					</div>
					<div class="model-footer">
						<slot name="footer">
							<button class="modal-default-button" @click="onClick">OK</button>
						</slot>
					</div>
				</div>
			</div>
		</div>
	</transition>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
	name: 'ModalWindow',
	props: {
		submitStatus: String,
	},
	methods: {
		onClick: function (event: Event) {
			this.$emit('close')
			location.reload()
		},
	},
})
</script>

<style lang="sass">
.modal-mask
  position: fixed
  z-index: 9998
  top: 0
  left: 0
  width: 100%
  height: 100%
  background-color: rgba(0, 0, 0, 0.5)
  display: table
  transition: opacity 0.3s ease

.modal-wrapper
  display: table-cell
  vertical-align: middle

.modal-container
  width: 300px
  margin: 0px auto
  padding: 20px 30px
  background-color: #fff
  border-radius: 10px
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33)
  transition: all 0.3s ease
  font-family: Helvetica, Arial, sans-serif

.modal-body
  margin: 20px 0
.modal-default-button
  float: right
  width: min-content
  appearance: none
  border: 0
  border-radius: 5px
  background: rgb(5, 5, 215)
  color: #fff
  padding: 8px 16px
  font-size: 16px
  &:hover
    background: rgb(129, 232, 243)
  &:focus
    outline: none
    box-shadow: 0 0 0 4px #cbd6ee
.model-footer
  height: 20px
.modal-enter
  opacity: 0

.modal-leave-active
  opacity: 0

.modal-enter .modal-container,
.modal-leave-active .modal-container
  -webkit-transform: scale(1.1)
  transform: scale(1.1)
</style>
