<script setup lang="ts">
const props = defineProps<{
	id: string;
	class?: string;
}>();
</script>

<template>
	<section class="section" :class="props.class" :id="props.id">
		<div class="section__wrapper">
			<slot />
		</div>
	</section>
</template>

<style lang="scss" scoped>
.section {
	padding: 10px 0;
	width: 100%;
	&__wrapper {
		margin: 0 auto;
		width: 100%;
	}
}
</style>