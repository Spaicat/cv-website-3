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

// Active menu element on the corresponding section when scrolling
function getPosY(elt: Element) {
	return window.scrollY + elt.getBoundingClientRect().top;
}

function handleScroll() {
	let scrollPos = window.scrollY;
	let eltList = Array.from(document.querySelectorAll(`.header__main .item`));
	eltList.forEach((elt) => {
		let child = elt.querySelector(":scope > a");
		if (child === null) return;
		let href = child.getAttribute("href");
		if (href === null) return;
		let refElt = document.querySelector(href);
		if (refElt === null) return;

		if (
			getPosY(refElt) - 300 <= scrollPos &&
			getPosY(refElt) + refElt.clientHeight > scrollPos
		) {
			if (!elt.classList.contains("active")) {
				eltList.forEach((elt) => elt.classList.remove("active"));
				elt.classList.add("active");
			}
		}
		else {
			elt.classList.remove("active");
		}
	});
}

window.addEventListener("scroll", handleScroll);
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
					<a
						class="link"
						href="download/CV.pdf"
						target="_blank"
						download
					>
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
	font-size: 14px;
	&__wrapper {
		position: relative;
		display: flex;
		flex-direction: column;
		overflow: hidden;
		margin: 1rem;
		list-style: none;
	}

	$logo-height: 25px;
	$logo-margin: 0.75rem;
	.hamburger {
		cursor: pointer;
		position: absolute;
		top: 0;
		right: 0;
		margin: $logo-margin;
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
		padding: $logo-margin;
		.logo {
			height: $logo-height;
			min-height: $logo-height;
		}
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
	&__main {
		display: flex;
		flex-direction: column;
		margin: auto 0;
		margin-top: 0.5rem;
	}

	.item {
		display: flex;
		margin-bottom: 0.25rem;

		$margin-link: 1rem;
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
		&:hover .link {
			color: var(--color-font);
			fill: var(--color-font);
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
				transform: translateX(0.6rem + $size-bullet);
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
		&__main,
		.item {
			margin: 0;
		}
		.hamburger {
			display: none;
		}
	}
}
</style>
