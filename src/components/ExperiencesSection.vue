<script setup lang="ts">
interface Experience {
	title: string;
	date: string;
	description: string;
}

const experiences: Experience[] = [
	{
		title: "Stage chez Inetum",
		date: "Avril 2021 - Juin 2021 (3 mois)",
		description:
			"J'ai pu intégrer une équipe dans une entreprise d'Inetum situé à Lyon 5eme. Mon stage s'est déroulé dans le service application de celle-ci, j'ai ainsi pu rejoindre une équipe qui s'occupait exclusivement du projet sur lequel j'ai travaillé durant la période de mon stage. J'ai intégré une équipe de 6 personnes. Mon travail durant ces trois mois de stage a été de participer à la réalisation d'une application web pour gérer les sous-concessionnaire des différentes aires d'autoroute du réseau autoroutier d'APRR. Je devais réaliser le développement d’écran de saisie d’activité, de suivi, de tableau de bord ou encore de paramétrage.",
	},
	{
		title: "Stage chez Fiducial",
		date: "Mai 2021 - Août 2022 (4 mois)",
		description:
			"J'ai pu intégrer une équipe dans une entreprise d'Inetum situé à Lyon 5eme. Mon stage s'est déroulé dans le service application de celle-ci, j'ai ainsi pu rejoindre une équipe qui s'occupait exclusivement du projet sur lequel j'ai travaillé durant la période de mon stage. J'ai intégré une équipe de 6 personnes. Mon travail durant ces trois mois de stage a été de participer à la réalisation d'une application web pour gérer les sous-concessionnaire des différentes aires d'autoroute du réseau autoroutier d'APRR. Je devais réaliser le développement d’écran de saisie d’activité, de suivi, de tableau de bord ou encore de paramétrage.",
	}
]
</script>

<template>
	<div class="experiences__container">
		<div class="experiences__header">
			<h2 class="section__title">Mes <span>expériences.</span></h2>
			<p class="section__subtitle">
				De l'apprentissage théorique à la mise en pratique : voici l'aperçu de mes opportunités de croissance professionnel.
			</p>
		</div>
		<div class="experiences__content">
			<div class="experiences__list">
				<div
					v-for="experience in experiences"
					:key="experience.title"
					class="experiences__item"
				>
					<div class="header">
						<h3 class="title">{{ experience.title }}</h3>
						<span class="date">{{ experience.date }}</span>
					</div>
					<p class="description">{{ experience.description }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
@import "../src/assets/functions.scss";
.experiences {
	&__container {
		display: flex;
		flex-direction: column;
		.section__title {
			text-align: left;
		}
	}
	&__header {
		margin-bottom: 20px;
	}
	&__list {
		$minWidth: 400px;
		$maxColumns: 2;
		$gap: 30px;
		@include dynamic-grid($minWidth, $maxColumns, $gap);
		width: 100%;
	}
	&__item {
		display: flex;
		align-items: center;
		flex-direction: column;
		padding: 30px;
		border-radius: 10px;
		width: 100%;
		max-width: 1070px;
		background-color: var(--color-background-2);
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
			flex-direction: column;
			width: 100%;
			.title {
				margin: 0;
				font-weight: 700;
				font-size: 28px;
				line-height: 1.4;
				word-break: break-word;
			}
			.date {
				color: var(--color-primary);
			}
		}
		.description {
			margin: 15px 0;
			font-size: 14px;
			color: var(--color-font-2);
			font-family: var(--font-secondary);
			word-break: break-word;
		}
	}
}

@media (min-width: 850px) {
	.experiences {
		&__container {
			flex-direction: row;
		}
		&__header {
			max-width: 350px;
			margin-right: 20px;
		}
	}
}
</style>
