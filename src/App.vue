<script setup lang="ts">
import { ref, computed } from "vue";

export type BATriangleCoords = {
	x: { from: number; to: number };
	y: { from: number; to: number };
};

import um from "./components/um.vue";
import BATriangle from "./components/BATriangle.vue";

const circle = ref<HTMLElement | null>(null);

const mouseX = ref<number>(0);
const mouseY = ref<number>(0);

const triangleCoords = ref(createTriangles());

const angleDeg = computed<number>(() => {
	const circleX = circle.value?.offsetLeft ?? 0;
	const circleY = circle.value?.offsetTop ?? 0;

	return +(
		(Math.atan2(mouseY.value - circleY, mouseX.value - circleX) * 180) /
		Math.PI
	).toFixed(2);
});

const translate = computed(() => {
	const radian = angleDeg.value * (Math.PI / 180);
	const distance = 50;

	const x = distance * Math.cos(radian);
	const y = distance * Math.sin(radian);

	return { x, y };
});

function createTriangles() {
	const triangles = Array.from({ length: 6 }, (_, __) => {
		const randomPi = Math.random() * Math.PI;
		const translateUp = Math.random() * 1 > 0.5 ? true : false;

		const distance = 40;
		const translateFrom = getTransformTranslateFromRadian(randomPi, distance);
		const translateTo = getTransformTranslateFromRadian(
			randomPi,
			distance + 30,
		);

		return {
			x: {
				from: translateFrom.x,
				to: translateTo.x,
			},
			y: {
				from: translateFrom.y * (translateUp ? -1 : 1),
				to: translateTo.y * (translateUp ? -1 : 1),
			},
		};
	});

	return triangles;
}

function getTransformTranslateFromRadian(radian: number, distance: number) {
	const x = distance * Math.cos(radian);
	const y = distance * Math.sin(radian);

	return { x, y };
}

function moveCircle(e: MouseEvent) {
	circle.value!.style.left = `${e.clientX}px`;
	circle.value!.style.top = `${e.clientY}px`;
	triangleCoords.value = createTriangles();
}

window.onclick = moveCircle;
window.onmousemove = (e) => {
	mouseX.value = e.clientX;
	mouseY.value = e.clientY;
};
</script>

<template>
	<div ref="circle" class="fixed grid place-items-center">
		<div
			class="absolute grid place-items-center rounded-full bg-cyan-300/50 p-8"
		>
			<svg
				:style="{ transform: `translate(${translate.x}px, ${translate.y}px` }"
				xmlns="http://www.w3.org/2000/svg"
				width="16"
				height="16"
				viewBox="0 0 24 24"
				class="absolute text-red-200/50"
			>
				<path fill="currentColor" d="M1 21h22L12 2" />
			</svg>

			<BATriangle v-for="triangle in triangleCoords" v-bind="triangle" />
		</div>

		<div class="absolute rounded-full bg-white p-1" />
	</div>
</template>

<style lang="postcss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;600;800&display=swap");

*,
*::before,
*::after {
	@apply m-0 box-border p-0;
}

body {
	@apply bg-stone-800 font-["Poppins",_sans-serrif] text-stone-300;
}

#app {
	@apply flex min-h-screen flex-col items-center justify-center py-10;
}
</style>

<style lang="scss">
.fade {
	&-enter-active,
	&-leave-active {
		transition: opacity 150ms;
	}

	&-enter-from,
	&-leave-to {
		opacity: 0;
	}
}
</style>
