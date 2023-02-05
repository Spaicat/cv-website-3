<script setup lang="ts">
import { computed } from "vue";

const getAge = computed(() => {
	let today = new Date();
	let birthDate = new Date("2000-09-18");
	let age = today.getFullYear() - birthDate.getFullYear();
	let month = today.getMonth() - birthDate.getMonth();
	if (month < 0 || (month === 0 && today.getDate() < birthDate.getDate()))
		age--;
	return age;
});
</script>

<template>
	<div class="about__container">
		<h2 class="section__title">À propos de <span>moi.</span></h2>
		<div class="columns__layout">
			<div class="text-column">
				<p>
					Je suis un étudiant en informatique et j'ai des compétences assez polyvalentes. Je suis <strong>passionné</strong> et <strong>motivé</strong> par mon travail tout en étant quelqu'un de <strong>persévérant</strong>. Depuis le collège, je m'intéresse justement au domaine de l'informatique et espère y travailler dans un futur proche. Je pense effectivement que l'informatique est un domaine essentiel dans notre développement et je veux ainsi y participer activement.
				</p>
			</div>
			<div class="details-column">
				<ul className="about-list">
					<li>
						<span>{{ getAge }} ans</span>
					</li>
					<li>
						<span>Francheville - 69340</span>
					</li>
					<li>
						<span>Permis B</span>
					</li>
					<li>
						<span>
							<a href="tel:33769461445" class="link">
								+33 7 69 46 14 45
							</a>
						</span>
					</li>
					<li>
						<span>
							<a
								href="mailto:trembleau.thibault@gmail.com"
								class="link"
							>
								trembleau.thibault@gmail.com
							</a>
						</span>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped>
.about__container {
	display: flex;
	flex-direction: column;
	.columns__layout {
		display: flex;
		flex-direction: column;
		align-items: center;
		& > *:first-child {
			margin-bottom: 2rem;
		}
	}
}

.details-column {
	width: 100%;
	.about-list {
		display: flex;
		flex-direction: column;
		margin: 0;
		padding: 0;
		li {
			display: flex;
			margin: 5px 0;
			padding: 5px 10px;
			align-items: center;
			list-style: none;
			word-break: break-word;
			border-radius: 6px;
			color: var(--color-primary);
			a {
				color: var(--color-primary);
			}
		}
	}
}
.text-column {
	width: 100%;
	p {
		margin: 0;
		padding: 30px;
		background-color: var(--color-background-2);
		border-radius: 10px;
		font-size: 12px;
		font-family: "JetBrains Mono", monospace;
	}
}

@media (min-width: 700px) {
	.text-column p {
		text-align: justify;
		padding: 40px 50px;
		font-size: 14px;
	}
}
@media (min-width: 900px) {
	.about__container {
		.columns__layout {
			flex-direction: row;
			& > *:first-child {
				margin-bottom: 0;
				margin-right: 2rem;
			}
			.details-column {
				width: 35%;
			}
			.text-column {
				width: 65%;
			}
		}
	}
}
</style>
