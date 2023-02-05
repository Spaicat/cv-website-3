<script setup lang="ts">
import SectionLayout from "@/components/SectionLayout.vue";
import HomeSection from "@/components/HomeSection.vue";
import AboutSection from "@/components/AboutSection.vue";
</script>

<template>
	<SectionLayout id="home" class="home">
		<HomeSection />
	</SectionLayout>
	<SectionLayout id="about">
		<AboutSection />
	</SectionLayout>
</template>

<style lang="scss">
.home {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	margin: 0;
	position: relative;
	overflow: hidden;
	color: var(--color-font);
	height: 750px;
	min-height: 100vh;
}
</style>
