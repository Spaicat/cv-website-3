<script setup lang="ts">
import { ref } from "vue";
import GithubLogo from "./icons/GithubLogo.vue";
import LinkedinLogo from "./icons/LinkedinLogo.vue";
import MailLogo from "./icons/MailLogo.vue";

interface Contact {
	id: number;
	icon: object;
	link: string;
}

const contacts: Contact[] = [
	{
		id: 1,
		icon: LinkedinLogo,
		link: "https://www.linkedin.com/in/thibault-trembleau/",
	},
	{
		id: 2,
		icon: GithubLogo,
		link: "https://github.com/Spaicat",
	},
	{
		id: 3,
		icon: MailLogo,
		link: "mailto:trembleau.thibault@gmail.com",
	},
];

const contactHovered = ref(-1);
</script>

<template>
	<div class="contact__container">
		<h2 class="section__title">Pour me <span>contacter.</span></h2>
		<ul class="contact__list">
			<li
				v-for="contact in contacts"
				:key="contact.link"
				class="contact__item"
			>
				<a
					:href="contact.link"
					class="contact__link"
					:class="contactHovered === contact.id ? 'hovered' : ''"
					target="_blank"
					@mouseover="contactHovered = contact.id"
					@mouseleave="contactHovered = -1"
				>
					<component
						:is="contact.icon"
						:colored="contactHovered === contact.id"
					/>
				</a>
			</li>
		</ul>
	</div>
</template>

<style lang="scss" scoped>
.contact {
	&__list {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		margin: 0;
		padding: 0;
	}
	&__item {
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0 15px 30px 15px;
	}
	&__link {
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 40px;
		border-radius: 10px;
		background-color: var(--color-background-2);
		border: 1px solid var(--color-background-3);
		transition: all 0.2s ease-in-out;
		&.hovered {
			background-color: var(--color-font);
		}
	}
}
svg {
	fill: var(--color-font);
	width: 100%;
	max-width: 135px;
}
</style>
