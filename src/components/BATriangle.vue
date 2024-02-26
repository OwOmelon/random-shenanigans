<script setup lang="ts">
import type { BATriangleCoords } from "../App.vue";

const props = defineProps<BATriangleCoords>();
</script>

<template>
	<svg
		xmlns="http://www.w3.org/2000/svg"
		width="16"
		height="16"
		viewBox="0 0 24 24"
		class="triangle-anim absolute text-cyan-200/50"
	>
		<path fill="currentColor" d="M1 21h22L12 2" />
	</svg>
</template>

<style scoped lang="postcss">
.triangle-anim {
	animation: triangle 1s ease-out infinite;
}

@keyframes triangle {
	from {
		transform: translate(v-bind(x.from + "px"), v-bind(y.from + "px"));
	}

	to {
		transform: translate(v-bind(x.to + "px"), v-bind(y.to + "px"));
	}
}
</style>
