<script setup lang="ts">
const props = defineProps<{
	color: string;
	name: string | number;
}>();
</script>

<template>
	<div class="rounded bg-white">
		<div
			:style="{ backgroundColor: color }"
			class="aspect-square rounded-t"
		></div>
		<p class="text-center text-sm text-black">{{ name }}: {{ color }}</p>
	</div>
</template>
