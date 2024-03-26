<template>
	<button class="c-button" type="submit">Создать</button>
</template>

<script lang="ts">
export default {
	name: 'Button',
}
</script>

<style lang="sass">
.c-button
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
</style>
