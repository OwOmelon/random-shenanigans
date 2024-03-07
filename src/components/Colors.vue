<script setup lang="ts">
import ColorCard from "./ColorCard.vue";

type Colors = {
	main: string;
	shades: {
		50: string;
		100: string;
		200: string;
		300: string;
		400: string;
		500: string;
		600: string;
		700: string;
		800: string;
		900: string;
		950: string;
	};
};

const template: Colors = {
	main: "",
	shades: {
		50: "",
		100: "",
		200: "",
		300: "",
		400: "",
		500: "",
		600: "",
		700: "",
		800: "",
		900: "",
		950: "",
	},
};

const colors: Record<string, Colors> = {
	text: {
		main: "#F1F2F2  ",
		shades: {
			50: "#f2f3f3",
			100: "#e4e7e7",
			200: "#cacece",
			300: "#afb6b6",
			400: "#959d9d",
			500: "#7a8585",
			600: "#626a6a",
			700: "#495050",
			800: "#313535",
			900: "#181b1b",
			950: "#0c0d0d",
		},
	},
	background: {
		main: "#111513 ",
		shades: {
			50: "#f1f4f2",
			100: "#e3e8e6",
			200: "#c6d2cc",
			300: "#aabbb3",
			400: "#8ea499",
			500: "#718e80",
			600: "#5b7166",
			700: "#44554d",
			800: "#2d3933",
			900: "#171c1a",
			950: "#0b0e0d",
		},
	},
	primary: {
		main: "#ABC1B7 ",
		shades: {
			50: "#f1f4f2",
			100: "#e3e8e6",
			200: "#c6d2cc",
			300: "#aabbb3",
			400: "#8ea499",
			500: "#718e80",
			600: "#5b7166",
			700: "#44554d",
			800: "#2d3933",
			900: "#171c1a",
			950: "#0b0e0d",
		},
	},
	secondary: {
		main: "#22322b ",
		shades: {
			50: "#f0f5f3",
			100: "#e0ebe6",
			200: "#c2d6cd",
			300: "#a3c2b5",
			400: "#85ad9c",
			500: "#669983",
			600: "#527a69",
			700: "#3d5c4f",
			800: "#293d34",
			900: "#141f1a",
			950: "#0a0f0d",
		},
	},
	accent: {
		main: "#78AA93 ",
		shades: {
			50: "#eff5f2",
			100: "#e0ebe6",
			200: "#c0d8cd",
			300: "#a1c4b4",
			400: "#82b09b",
			500: "#629d81",
			600: "#4f7d68",
			700: "#3b5e4e",
			800: "#273f34",
			900: "#141f1a",
			950: "#0a100d",
		},
	},
};
</script>

<template>
	<div class="flex flex-col gap-2">
		<div
			v-for="(content, type, i1) in colors"
			class="rounded border-[1px] border-white p-1 bg-white/10"
		>
			<ColorCard :color="content.main" :name="type" class="w-[100px] mx-auto mb-5" />

			<div class="grid grid-cols-[repeat(11,_minmax(0,_1fr))] gap-2">
				<ColorCard
					v-for="(hex, shade, i2) in content.shades"
					:name="shade"
					:color="hex"
				/>
			</div>
		</div>
	</div>
</template>
