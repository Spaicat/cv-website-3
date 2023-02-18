<script setup lang="ts">
import { ref, computed } from "vue";
import HTMLCSSLogo from "./icons/skills/HTMLCSSLogo.vue";
import JSLogo from "./icons/skills/JSLogo.vue";
import SassLogo from "./icons/skills/SassLogo.vue";
import PHPLogo from "./icons/skills/PHPLogo.vue";
import TypescriptLogo from "./icons/skills/TypescriptLogo.vue";
import ReactLogo from "./icons/skills/ReactLogo.vue";
import NextLogo from "./icons/skills/NextLogo.vue";
import VueLogo from "./icons/skills/VueLogo.vue";
import NodeLogo from "./icons/skills/NodeLogo.vue";
import SvelteLogo from "./icons/skills/SvelteLogo.vue";
import CSharpLogo from "./icons/skills/CSharpLogo.vue";
import CppLogo from "./icons/skills/CppLogo.vue";
import CLogo from "./icons/skills/CLogo.vue";
import PythonLogo from "./icons/skills/PythonLogo.vue";
import JavaLogo from "./icons/skills/JavaLogo.vue";
import MySqlLogo from "./icons/skills/MySqlLogo.vue";
import PostgreSqlLogo from "./icons/skills/PostgreSqlLogo.vue";
import PLSqlLogo from "./icons/skills/PLSqlLogo.vue";
import MongoDBLogo from "./icons/skills/MongoDBLogo.vue";
import PhotoshopLogo from "./icons/skills/PhotoshopLogo.vue";
import IllustratorLogo from "./icons/skills/IllustratorLogo.vue";
import PremiereProLogo from "./icons/skills/PremiereProLogo.vue";
import XDLogo from "./icons/skills/XDLogo.vue";
import FigmaLogo from "./icons/skills/FigmaLogo.vue";

interface Category {
	id: string;
	title: string;
}

const categories: Category[] = [
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

interface Skill {
	title: string;
	categoryId: string;
	icon: string | object;
	colorIcon: string;
	colorBackground: string;
}

const skills: Skill[] = [
	{
		title: "HTML/CSS",
		categoryId: "web",
		icon: HTMLCSSLogo,
		colorIcon: "white",
		colorBackground: "#f06529",
	},
	{
		title: "Sass",
		categoryId: "web",
		icon: SassLogo,
		colorIcon: "white",
		colorBackground: "#CD6799",
	},
	{
		title: "PHP",
		categoryId: "web",
		icon: PHPLogo,
		colorIcon: "white",
		colorBackground: "#787cb4",
	},
	{
		title: "Javascript",
		categoryId: "web",
		icon: JSLogo,
		colorIcon: "#323330",
		colorBackground: "#F0DB4F",
	},
	{
		title: "Typescript",
		categoryId: "web",
		icon: TypescriptLogo,
		colorIcon: "white",
		colorBackground: "#3178c6",
	},
	{
		title: "React.js",
		categoryId: "web",
		icon: ReactLogo,
		colorIcon: "#1c2c4c",
		colorBackground: "#61DBFB",
	},
	{
		title: "Next.js",
		categoryId: "web",
		icon: NextLogo,
		colorIcon: "white",
		colorBackground: "black",
	},
	{
		title: "Vue.js",
		categoryId: "web",
		icon: VueLogo,
		colorIcon: "white",
		colorBackground: "#42b883",
	},
	{
		title: "Svelte.js",
		categoryId: "web",
		icon: SvelteLogo,
		colorIcon: "white",
		colorBackground: "#ff3c00",
	},
	{
		title: "Node.js",
		categoryId: "web",
		icon: NodeLogo,
		colorIcon: "white",
		colorBackground: "#68a063",
	},
	{
		title: "C#",
		categoryId: "software",
		icon: CSharpLogo,
		colorIcon: "white",
		colorBackground: "#a179dc",
	},
	{
		title: "C",
		categoryId: "software",
		icon: CLogo,
		colorIcon: "white",
		colorBackground: "#5f98cf",
	},
	{
		title: "C++",
		categoryId: "software",
		icon: CppLogo,
		colorIcon: "white",
		colorBackground: "#5f98cf",
	},
	{
		title: "Java",
		categoryId: "software",
		icon: JavaLogo,
		colorIcon: "white",
		colorBackground: "#ec2024",
	},
	{
		title: "Python",
		categoryId: "software",
		icon: PythonLogo,
		colorIcon: "white",
		colorBackground: "#306998",
	},
	{
		title: "MySQL",
		categoryId: "db",
		icon: MySqlLogo,
		colorIcon: "white",
		colorBackground: "#00618a",
	},
	{
		title: "PostgreSQL",
		categoryId: "db",
		icon: PostgreSqlLogo,
		colorIcon: "white",
		colorBackground: "#2f6792",
	},
	{
		title: "PL/SQL",
		categoryId: "db",
		icon: PLSqlLogo,
		colorIcon: "white",
		colorBackground: "#f80000",
	},
	{
		title: "MongoDB",
		categoryId: "db",
		icon: MongoDBLogo,
		colorIcon: "white",
		colorBackground: "#3fa037",
	},
	{
		title: "Adobe Photoshop",
		categoryId: "design",
		icon: PhotoshopLogo,
		colorIcon: "#30a8ff",
		colorBackground: "#001e36",
	},
	{
		title: "Adobe Illustrator",
		categoryId: "design",
		icon: IllustratorLogo,
		colorIcon: "#fe9900",
		colorBackground: "#340000",
	},
	{
		title: "Adobe Premiere Pro",
		categoryId: "design",
		icon: PremiereProLogo,
		colorIcon: "#d473f6",
		colorBackground: "#252654",
	},
	{
		title: "Adobe XD",
		categoryId: "design",
		icon: XDLogo,
		colorIcon: "#ff61f6",
		colorBackground: "#470137",
	},
	{
		title: "Figma",
		categoryId: "design",
		icon: FigmaLogo,
		colorIcon: "white",
		colorBackground: "#ff3a00",
	},
];

class SkillsGroup {
	id: string;
	skills: Skill[];

	constructor(id: string) {
		this.id = id;
		this.skills = [];
	}
}

const skillsByCategory = computed(() =>
	skills.reduce((memo: SkillsGroup[], obj: Skill) => {
		let objKey: string = obj.categoryId;
		let group: SkillsGroup | undefined = memo.find((x) => x.id === objKey);

		if (!group) {
			group = new SkillsGroup(objKey);
			memo.push(group);
		}
		group?.skills.push(obj);
		return memo;
	}, [])
);

const categoryOpened = ref("web");

function handleCategory(id: string) {
	categoryOpened.value = id;
}
</script>

<template>
	<div class="skills__container">
		<h2 class="section__title">Mes <span>compétences.</span></h2>
		<div class="skills__layout">
			<div class="skills__header">
				<ul class="menu">
					<li
						v-for="category in categories"
						class="menu__item"
						:class="[
							category.id === categoryOpened ? 'active' : '',
						]"
						:key="category.id"
						@click="handleCategory(category.id)"
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
			<div
				v-for="category in skillsByCategory"
				class="skills__content"
				:class="[category.id === categoryOpened ? 'active' : '']"
				:id="'category-' + category.id"
				:key="category.id"
			>
				<li
					class="skills__item"
					v-for="skill in category.skills"
					:key="skill.title"
				>
					<div
						class="skills__item--icon"
						:style="{
							'background-color': skill.colorBackground,
							fill: skill.colorIcon,
							stroke: skill.colorIcon,
						}"
					>
						<component :is="skill.icon" />
					</div>
					<span class="skills__item--title">{{ skill.title }}</span>
				</li>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@import "../src/assets/functions.scss";
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
				cursor: pointer;
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
		$minWidth: 150px;
		$maxColumns: 5;
		$gap: 10px;
		@include dynamic-grid($minWidth, $maxColumns, $gap);
		display: none;
		padding: 20px;
		width: 100%;
		&.active {
			display: grid;
		}
		.skills__item {
			@include flex-center;
			flex-direction: column;
			background-color: var(--color-background-2);
			border-radius: 10px;
			padding: 20px;
			word-break: break-word;
			&--icon {
				@include flex-center;
				flex-direction: row;
				padding: 15px;
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
