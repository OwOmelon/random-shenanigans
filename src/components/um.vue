<script setup lang='ts'>
import { ref } from 'vue'

const color = ref('red')
const fontSize = ref(40)
</script>

<template>
	<p class="bind-color">man what in the goddamn</p>
</template>

<style scoped lang="postcss">
.bind-color {
	color: v-bind(color);
	font-size: v-bind(fontSize + 'px')
}
</style>