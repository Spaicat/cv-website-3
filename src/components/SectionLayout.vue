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

<style lang="scss">
.section {
	padding: 10px 0;
	width: 100%;

	&__wrapper {
		margin: 6rem auto;
		padding: 0 10px;
		width: 100%;
		max-width: 1300px;
	}
	&__title {
		font-size: 24px;
		font-weight: 900;
		span {
			font-weight: 900;
			color: var(--color-primary);
		}
	}
}

@media (min-width: 700px) {
	.section {
		&__wrapper {
			margin: 8rem auto;
		}
		&__title {
			font-size: 36px;
		}
	}
}
</style>