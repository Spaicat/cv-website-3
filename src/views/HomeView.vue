<script setup lang="ts">
import SectionLayout from "@/components/SectionLayout.vue";
import HomeSection from "@/components/HomeSection.vue";
import AboutSection from "@/components/AboutSection.vue";
import SkillsSection from "@/components/SkillsSection.vue";
import ProjectsSection from "@/components/ProjectsSection.vue";
import ExperiencesSection from "@/components/ExperiencesSection.vue";
</script>

<template>
	<SectionLayout id="home" class="home">
		<HomeSection />
	</SectionLayout>
	<SectionLayout id="about">
		<AboutSection />
	</SectionLayout>
	<SectionLayout id="skills">
		<SkillsSection />
	</SectionLayout>
	<SectionLayout id="projects">
		<ProjectsSection />
	</SectionLayout>
	<SectionLayout id="experiences">
		<ExperiencesSection />
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
