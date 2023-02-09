<script setup lang="ts">
const categories = [
	{
		id: "web",
		title: "Web",
	},
	{
		id: "software",
		title: "Dévelopement logiciel",
	},
	{
		id: "db",
		title: "Base de données",
	},
	{
		id: "design",
		title: "Design",
	},
];

const skills = [
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: "icon-dev",
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
];
</script>

<template>
	<div class="skills__container">
		<h2 class="section__title">Mes <span>compétences.</span></h2>
		<div class="skills__layout">
			<div class="skills__header">
				<ul class="menu">
					<li
						v-for="(category, index) in categories"
						class="menu__item"
						:class="[index === 0 ? 'active' : '']"
						:key="category.id"
					>
						{{ category.title }}
					</li>
				</ul>
				<div class="top-btns">
					<div class="top-btn"></div>
					<div class="top-btn"></div>
					<div class="top-btn"></div>
				</div>
			</div>
			<div class="skills__content">
				<li
					class="skills__item"
					v-for="skill in skills"
					:key="skill.title"
				>
					<div class="skills__item--icon">
						<!-- Add svg -->
					</div>
					<span class="skills__item--title">{{ skill.title }}</span>
				</li>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@mixin flex-center {
	display: flex;
	align-items: center;
	justify-content: center;
}
.skills {
	&__layout {
		@include flex-center;
		flex-direction: column;
		border-radius: 10px;
		border: 1px solid var(--color-background-3);
	}
	&__header {
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-direction: row;
		border-bottom: 1px solid var(--color-background-3);
		padding: 10px;
		width: 100%;
		.menu {
			display: flex;
			flex-direction: column;
			padding: 0;
			margin: 0;
			.menu__item {
				color: var(--color-font);
				margin-right: 10px;
				padding: 5px 15px;
				border-radius: 8px;
				list-style: none;
				word-break: break-word;
				&.active {
					color: var(--color-background-3);
					background-color: var(--color-font);
				}
			}
		}
		.top-btns {
			@include flex-center;
			flex-direction: row;
			.top-btn {
				margin-left: 5px;
				width: 15px;
				height: 15px;
				border-radius: 50%;
				background-color: var(--color-background-3);
			}
		}
	}
	&__content {
		display: grid;
		$minWidth: 150px;
		$maxColumns: 5;
		$gap: 10px;
		grid-template-columns: repeat(
			auto-fit,
			minmax(
				max($minWidth, (100% - ($gap * $maxColumns)) / $maxColumns),
				1fr
			)
		);
		grid-gap: $gap;
		padding: 20px;
		width: 100%;
		.skills__item {
			@include flex-center;
			flex-direction: column;
			background-color: var(--color-background-2);
			border-radius: 10px;
			padding: 20px;
			&--icon {
				@include flex-center;
				flex-direction: row;
				width: 90px;
				height: 90px;
				border-radius: 50%;
				background-color: var(--color-background-3);
			}
			&--title {
				margin-top: 10px;
				color: var(--color-font);
				font-size: 16px;
				font-weight: bold;
				font-family: var(--font-secondary);
			}
		}
	}
}

@media (min-width: 700px) {
	.skills {
		&__header {
			.menu {
				flex-direction: row;
				.menu__item {
					margin-right: 20px;
				}
			}
		}
	}
}
@media (max-width: 270px) {
	.skills__header .top-btns {
		display: none;
	}
}
</style>
