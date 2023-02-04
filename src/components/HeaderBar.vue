<script setup lang="ts">
import { ref } from "vue";

const links = [
	{ to: "#home", text: "Accueil" },
	{ to: "#about", text: "À propos" },
	{ to: "#skills", text: "Compétences" },
	{ to: "#projects", text: "Projets" },
	{ to: "#experiences", text: "Experiences" },
	{ to: "#contact", text: "Contact" },
];

const isMenuOpen = ref(false);

function toggleMenu() {
	isMenuOpen.value = !isMenuOpen.value;
}
</script>

<template>
	<header class="header">
		<div class="header__wrapper">
			<button class="hamburger" @click="toggleMenu">
				{{ isMenuOpen ? "FERMER" : "MENU" }}
			</button>
			<a href="/" class="header__logo">
				<img class="logo" src="@/assets/logo.svg" alt="Vue logo" />
			</a>
			<div class="header__menu" :class="[isMenuOpen ? 'menu-open' : '']">
				<nav class="header__main">
					<li
						class="item"
						:class="[link.to === '#home' ? 'active' : '']"
						v-for="link in links"
						:key="link.to"
					>
						<a class="link" :href="link.to">
							<span>{{ link.text }}</span>
						</a>
					</li>
				</nav>
				<li class="item">
					<a class="link" href="#" target="_blank" download>
						<span>Télécharger CV</span>
					</a>
				</li>
			</div>
		</div>
	</header>
</template>

<style lang="scss" scoped>
@use "sass:math";

@function pxToRem($pxValue) {
	@return math.div($pxValue, 16px) * 1rem;
}

.header {
	position: fixed;
	top: 0;
	left: 0;
	z-index: 100;
	display: flex;
	flex-direction: column;
	width: 100%;
	background-color: var(--color-background-2);
	&__wrapper {
		position: relative;
		display: flex;
		flex-direction: column;
		overflow: hidden;
		margin: 1rem;
		list-style: none;
	}

	$logo-height: 50px;
	.hamburger {
		position: absolute;
		top: 0;
		right: 0;
		margin: 1rem;
		padding: 0;
		height: $logo-height;
		background: none;
		border: none;
		color: var(--color-font-2);
		font-weight: 500;
		letter-spacing: 0.1rem;
	}

	&__logo {
		display: inline-flex;
		align-self: flex-start;
		padding: 1rem;
		.logo {
			height: $logo-height;
			min-height: $logo-height;
		}
	}
	&__main {
		display: flex;
		flex-direction: column;
		margin: auto 0;
	}
	&__menu {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		width: 100%;
		max-height: 0;
		transition: all 0.3s ease-in-out;
		&.menu-open {
			max-height: 500px;
		}
	}

	.item {
		display: flex;
		margin-bottom: 0.25rem;

		$margin-link: 0.6rem;
		.link {
			position: relative;
			display: flex;
			align-items: center;
			padding: 0.4rem;
			color: var(--color-font-2);
			fill: var(--color-font-2);
			&::before {
				content: "";
				position: absolute;
				width: 0;
				height: 0;
				margin-left: $margin-link;
				border-radius: 50%;
				background-color: var(--color-primary);
			}
			span {
				display: inline-flex;
				justify-content: center;
				align-items: center;
				margin: 0 $margin-link;
				white-space: nowrap;
				transform: translateX(0);
				font-weight: 500;
			}
			&::before,
			span {
				transition: all 0.15s;
			}
		}
		&.active .link {
			color: var(--color-font);
			fill: var(--color-font);

			$size-bullet: pxToRem(8px);
			&::before {
				width: $size-bullet;
				height: $size-bullet;
			}
			span {
				transform: translateX($margin-link + $size-bullet);
			}
		}
	}
}

@media (min-width: 900px) {
	.header {
		&__wrapper,
		&__menu,
		&__main {
			flex-direction: row;
			max-height: inherit;
		}
		.item {
			margin: 0;
		}
		.hamburger {
			display: none;
		}
	}
}
</style>
