<script setup lang="ts">
</script>

<template>
	<div class="home__container">
		<div class="box-left">
			<h1 class="home__title">Thibault <br /> Trembleau</h1>
			<h2 class="home__subtitle">Etudiant en informatique</h2>
			<p>
				Etudiant en 3ème année de licence informatique, je suis à la recherche d'un travail de 2 à 4 mois entre Mai et Août 2022
			</p>
		</div>
		<div class="box-right"></div>
	</div>
</template>

<style lang="scss" scoped>
.home {
	&__container {
		display: -ms-grid;
		display: grid;
		padding: 4rem 0;
		align-items: center;

		.box-left {
			-ms-grid-row: 1;
			grid-row: 1;
		}
		.box-right {
			-ms-grid-row: 2;
			grid-row: 2;
		}
		p {
			max-width: 700px;
			margin: 40px 0;
			color: var(--color-font-2);
		}
	}

	&__title {
		font-size: 40px;
		font-weight: 900;
		line-height: 1.1;
		margin-top: 0;
		margin-bottom: 14px;
		color: var(--color-font);
		br {
			display: none;
		}
	}
	&__subtitle {
		margin: 0;
		font-size: 20px;
		font-weight: 200;
		color: var(--color-primary);
	}
}
@media (min-width: 700px) {
	.home__title {
		font-size: 48px;
	}
}
@media (min-width: 900px) {
	.home {
		&__container {
			-ms-grid-columns: 80% 1fr;
			grid-template-columns: 80% 1fr;
			padding: 0 15px;
			text-align: left;
			p {
				margin-left: 0;
				margin-right: 0;
			}
			.box-right {
				-ms-grid-row: 1;
				grid-row: 1;
				-ms-grid-column: 2;
				grid-column: 2;
			}
		}
		&__title {
			font-size: 56px;
			br {
				display: inline;
			}
		}
	}
}
</style>
