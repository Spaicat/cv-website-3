<script setup lang="ts">
import bkecoImage from "@/assets/projects/bkeco_mockup.png";
import patrimoineImage from "@/assets/projects/patrimoine_mockup.png";
import movieRecommandationImage from "@/assets/projects/movie_recommandation.png";
import pathMazeVisualizerImage from "@/assets/projects/path_maze_visualizer.png";
import PlayIcon from "./icons/PlayIcon.vue";
import GithubIcon from "./icons/GithubIcon.vue";

interface Project {
	title: string;
	date: string;
	category: string;
	nbGroup: number | null;
	description: string;
	technologies: string[];
	links?: {
		github?: string;
		run?: string;
	};
}

interface BigProject extends Project {
	type: "BIG";
	image: {
		src: string;
		alt: string;
	};
}

interface SmallProject extends Project {
	type: "SMALL";
	icon: object | string;
}

const projects: (BigProject | SmallProject)[] = [
	{
		type: "BIG",
		title: "Pathfinder et génération de labyrinthe",
		date: "2022",
		category: "Projet personnel",
		image: {
			src: pathMazeVisualizerImage,
			alt: "Visualisation du pathfinding et de la génération de labyrinthe",
		},
		nbGroup: 1,
		description:
			"Site internet pour visualiser différents algorithmes de génération de labyrinthes et de pathfinding pour les résoudre.",
		technologies: ["HTML/CSS", "JS"],
		links: {
			run: "https://spaicat.github.io/Pathfinding/",
			github: "https://github.com/Spaicat/Pathfinding",
		},
	},
	{
		type: "BIG",
		title: "Application de recommandation de films",
		date: "Mars 2022 - Mai 2022",
		category: "Projet d'école",
		image: {
			src: movieRecommandationImage,
			alt: "Application de recommandation de films.",
		},
		nbGroup: 3,
		description:
			"Application pour recommander des films selon les actions de l'utilisateur, avec un côté interface utilisateur et un côté serveur pour les algorithmes de recommandation.",
		technologies: ["HTML", "Sass", "JS", "Vue.js", "Electron", "Python"],
		links: {
			github: "https://github.com/PreslavPO/Recommandation-de-contenu",
		},
	},
	{
		type: "BIG",
		title: "Site présentation de commerce",
		date: "Avril 2021 - Mai 2021",
		category: "Projet personnel",
		image: {
			src: bkecoImage,
			alt: "projet présentation commerce",
		},
		nbGroup: 1,
		description:
			"Réalisation d'un site internet pour un prestataire de service de renovation d'intérieur. Ce site à été fait seul en colaboration avec le propriétaire du site (Mise en commun du design et du contenu avec Adobe Xd).",
		technologies: ["HTML/CSS", "JS", "PHP"],
		links: {
			run: "http://www.bkeco.fr",
		},
	},
	{
		type: "BIG",
		title: "Digitalisation patrimoine historique",
		date: "Octobre 2020 - Janvier 2021",
		category: "Projet d'école",
		image: {
			src: patrimoineImage,
			alt: "projet digitalisation patrimoine historique",
		},
		nbGroup: 8,
		description:
			"Le but de ce projet était de créer un outil pour aider des médiévistes dans leur étude des dons des Ducs de France au XVème siècle.\r\n\n Nous avons réalisé une base de données pour remplacer leur Excel, un outil pour transférer le contenu de cet Excel dans la base de données et surtout un site internet sur lequel une fois connecté, ils peuvent ajouter, supprimer et modifier un don et voir une représentation des données sous plusieurs formes utiles à l’analyse : Une restitution sous forme de texte triée par bénéficiaire, une carte des lieux de dons et un calendrier qui trie les dons par date",
		technologies: ["HTML/CSS", "JS", "PHP", "SQL", "Python"],
	},
	{
		type: "SMALL",
		title: "Carnet de santé en ligne",
		date: "Février 2021 - Avril 2021",
		category: "Projet d'école",
		icon: GithubIcon,
		nbGroup: 6,
		description: "",
		technologies: ["HTML/CSS", "JS", "Node.js", "React.js", "MongoDB"],
	},
	{
		type: "SMALL",
		title: "Création d'un prologiciel",
		date: "Octobre 2020 - Janvier 2021",
		category: "Projet d'école",
		icon: GithubIcon,
		nbGroup: 4,
		description:
			"Ce projet avait pour but de nous faire réaliser une application de gestion de projet pour une entreprise (l'entreprise était factice) afin de nous mettre dans le cadre d'une vraie demande de projet réalisé en entreprise.",
		technologies: ["Java (Swing)", "SQL"],
	},
	{
		type: "SMALL",
		title: "Site web de présentation de l'IUT",
		date: "Octobre 2019 - Janvier 2020",
		category: "Projet d'école",
		icon: GithubIcon,
		nbGroup: 3,
		description:
			"Ce projet était un site internet ayant pour objectif de présenter l'IUT aux étudiants venant aux portes ouvertes de l'IUT. Ainsi de notre côté, nous avons décidé de s'orienter vers un style s'approchant de l'univers vidéoludique.",
		technologies: ["HTML/CSS", "JS", "PHP"],
	},
	{
		type: "SMALL",
		title: "Jeu-vidéo avec Unity3D",
		date: "Janvier 2019 - Juin 2019",
		category: "Projet d'école",
		icon: GithubIcon,
		nbGroup: 4,
		description:
			"Ce projet est un jeu vidéo que nous avons dû réaliser sur le moteur de jeu Unity3D. Nous avons donc créé tout le concept de celui-ci afin de pouvoir le coder.",
		technologies: ["C# (Moteur Unity3D)", "HTML/CSS", "PHP"],
	},
];

const smallProjects = projects.filter(
	(x: BigProject | SmallProject): x is SmallProject => x.type === "SMALL"
) as SmallProject[];

const bigProjects = projects.filter(
	(x: BigProject | SmallProject): x is BigProject => x.type === "BIG"
) as BigProject[];
</script>

<template>
	<div class="projects__container">
		<h2 class="section__title">Mes <span>projets.</span></h2>
		<div class="projects__layout">
			<div class="projects__list big">
				<div
					v-for="project in bigProjects"
					:key="project.title"
					class="projects__item big"
				>
					<a class="image" :href="project.links?.run" target="_blank">
						<img
							:src="project.image.src"
							:alt="project.image.alt"
						/>
					</a>
					<div class="details">
						<div class="header">
							<div class="title__container">
								<h3 class="title">{{ project.title }}</h3>
								<div class="subtitle">
									<span class="date">{{ project.date }}</span>
									<span class="category">{{ project.category }}</span>
								</div>
							</div>
							<div class="actions__container">
								<a
									v-if="project.links?.github"
									:href="project.links.github"
									target="_blank"
									class="action"
								>
									<GithubIcon />
								</a>
								<a
									v-if="project.links?.run"
									:href="project.links.run"
									target="_blank"
									class="action"
								>
									<PlayIcon />
								</a>
							</div>
						</div>
						<p class="description">{{ project.description }}</p>
						<div class="technologies__container">
							<span
								v-for="technology in project.technologies"
								:key="technology"
								class="technology"
							>
								{{ technology }}
							</span>
						</div>
					</div>
				</div>
			</div>
			<div class="projects__list small">
				<div
					v-for="project in smallProjects"
					:key="project.title"
					class="projects__item small"
				>
					<div class="icon__wrapper">
						<div class="icon">
							<component :is="project.icon" />
						</div>
						<div class="actions__container">
							<a
								v-if="project.links?.github"
								:href="project.links.github"
								target="_blank"
								class="action"
							>
								<GithubIcon />
							</a>
							<a
								v-if="project.links?.run"
								:href="project.links.run"
								target="_blank"
								class="action"
							>
								<PlayIcon />
							</a>
						</div>
					</div>
					<div class="details">
						<div class="header">
							<div class="title__container">
								<h3 class="title">{{ project.title }}</h3>
								<div class="subtitle">
									<span class="date">{{ project.date }}</span>
									<span class="category">{{ project.category }}</span>
								</div>
							</div>
						</div>
						<p class="description">{{ project.description }}</p>
						<div class="technologies__container">
							<span
								v-for="technology in project.technologies"
								:key="technology"
								class="technology"
							>
								{{ technology }}
							</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@import "../src/assets/functions.scss";
.projects {
	&__layout {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	&__list {
		width: 100%;
		&.big {
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			margin-bottom: 70px;
		}
		&.small {
			$minWidth: 350px;
			$maxColumns: 3;
			$gap: 30px;
			@include dynamic-grid($minWidth, $maxColumns, $gap);
		}
	}
	&__item {
		display: flex;
		align-items: center;
		border-radius: 10px;
		width: 100%;
		max-width: 1070px;
		.details {
			display: flex;
			flex-direction: column;
			height: 100%;
		}
		.actions__container {
			display: flex;
			flex-direction: row;
			padding: 10px;
			margin-left: auto;
			.action {
				width: 24px;
				height: 24px;
				color: var(--color-font-2);
				fill: var(--color-font-2);
				margin-left: 10px;
				&:first-child {
					margin-left: 0;
				}
				svg {
					width: 100%;
					height: 100%;
				}
				&:hover {
					fill: var(--color-primary);
				}
			}
		}
		.header {
			display: flex;
			flex-direction: row;
			justify-content: space-between;
			align-items: center;
			.title__container {
				display: flex;
				flex-direction: column;
				.title {
					margin: 0;
					font-weight: 700;
					font-size: 28px;
					line-height: 1.4;
					word-break: break-word;
				}
				.subtitle {
					color: var(--color-primary);
					.date::after {
						content: " • ";
					}
				}
			}
		}
		.description {
			margin: 15px 0;
			font-size: 14px;
			color: var(--color-font-2);
			font-family: var(--font-secondary);
			word-break: break-word;
		}
		.technologies__container {
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			flex-wrap: wrap;
			margin-top: auto;
			.technology {
				margin-right: 10px;
				margin-top: 10px;
				padding: 4px 8px;
				border-radius: 5px;
				background-color: var(--color-background-3);
				color: var(--color-primary);
				font-family: var(--font-secondary);
				font-size: 14px;
			}
		}

		&.big {
			flex-direction: column;
			margin-bottom: 50px;
			.image {
				display: flex;
				justify-content: center;
				align-items: center;
				overflow: hidden;
				width: 100%;
				height: 300px;
				border-radius: 10px;
				transition: transform 0.2s ease-in-out;
				img {
					width: 100%;
					height: 100%;
					object-fit: cover;
				}
				&:hover[href] {
					transform: translateY(-15px);
				}
			}
			.details {
				margin-top: 10px;
				width: 100%;
			}
		}
		&.small {
			flex-direction: column;
			padding: 30px;
			background-color: var(--color-background-2);
			border: 1px solid var(--color-background-3);
			.icon__wrapper {
				display: flex;
				align-items: center;
				width: 100%;
				margin-bottom: 20px;
				.icon {
					display: flex;
					padding: 13px;
					border-radius: 9px;
					background-color: var(--color-background);
					fill: var(--color-font);
					svg {
						width: 32px;
						height: 32px;
					}
				}
			}
		}
	}
}

@media (min-width: 700px) {
	.projects {
		&__item {
			&.big {
				flex-direction: row;
				.image {
					width: 80%;
					height: 100%;
					max-height: 250px;
				}
				.details {
					margin-top: 0;
					margin-left: 50px;
				}
			}
		}
	}
}

@media (max-width: 350px) {
	.projects__item {
		&.big {
			.image {
				height: 200px;
			}
		}
	}
}
</style>
