<script setup lang="ts">
import { ref, computed } from "vue";

import BaTriFx from "./components/BaTriFx.vue";
import Colors from "./components/Colors.vue";
</script>

<template>
	<!-- <BaTriFx /> -->
	<Colors />
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
