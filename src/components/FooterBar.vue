<script setup lang="ts"></script>

<template>
	<footer class="footer">
		<span>Site réalisé avec Vue.js et sass</span>
		<span>©2023 Thibault Trembleau</span>
	</footer>
</template>

<style lang="scss" scoped>
.footer {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	padding: 40px;
	font-family: var(--font-secondary);
	background-color: var(--color-background-2);
	> span {
		margin-top: 10px;
		:first-child {
			margin-top: 0;
		}
	}
}
</style>
