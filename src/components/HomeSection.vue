<script setup lang="ts">
</script>

<template>
	<div class="home__container">
		<div class="box-left">
			<h1 class="home__title">
				Thibault <br />
				Trembleau
			</h1>
			<h2 class="home__subtitle">Etudiant en Master Informatique</h2>
			<p>
				Etudiant en 1ère année de master informatique, je suis à la recherche d'une alternance pour l'année 2023-2024.
			</p>
			<div class="home__btns">
				<a class="button" href="#contact">
					<span>Me contacter</span>
				</a>
				<a
					class="button"
					href="/download/CV.pdf"
					target="_blank"
					download
				>
					<span>Mon CV</span>
				</a>
			</div>
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
	}

	&__title {
		font-size: 40px;
		font-weight: 900;
		line-height: 1.1;
		margin-top: 0;
		margin-bottom: 10px;
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
	p {
		max-width: 700px;
		margin-top: 30px;
		margin-bottom: 30px;
		color: var(--color-font-2);
	}
	&__btns {
		display: flex;
		.button {
			margin-right: 15px;
		}
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
