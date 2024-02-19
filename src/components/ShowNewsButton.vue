<script setup>
const props = defineProps({
	showAllArticles: Boolean,
	toggleArticles: Function
});
</script>

<template>
	<button :class="{ 'show-news-button--active': showAllArticles }" class="show-news-button"
		@click="toggleArticles" :aria-pressed="showAllArticles ? 'true' : 'false'">
		Show news
	</button>
</template>

<style scoped>
.show-news-button {
	color: var(--tg-theme-button-text-color);
	background-color: var(--tg-theme-button-color);
	padding: 15px 0;
	font-size: 20px;
	width: 100%;
	border: none;
	position: relative;
	cursor: pointer;
}

.show-news-button::after {
	position: absolute;
	content: '';
	width: 0px;
	height: 0px;
	top: 50%;
	margin-left: 10px;
	border-style: solid;
	border-width: 10px 7.5px 0 7.5px;
	border-top-color: var(--tg-theme-button-text-color);
	border-left-color: transparent;
	border-right-color: transparent;
	border-bottom-color: transparent;
	transform: translateY(-50%) rotate(0deg);
}

.show-news-button--active::after {
	transform: translateY(-50%) rotate(180deg);
}
</style>
