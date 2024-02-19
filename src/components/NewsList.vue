<script setup>
import { ref } from 'vue';
import Article from './Article.vue';
import ShowNewsButton from './ShowNewsButton.vue'

const props = defineProps({
	data: Object,
})

const showAllArticles = ref(false);

const toggleArticles = () => {
	showAllArticles.value = !showAllArticles.value
}

</script>

<template>
	<ShowNewsButton :showAllArticles="showAllArticles" :toggleArticles="toggleArticles" />

	<ul :class="{ 'news-list--active': showAllArticles }" class="news-list">
		<li v-for="article in data" :key="item">
			<Article :title="article.title" :description="article.description" :image="article.image" />
		</li>
	</ul>
</template>

<style scoped>
.news-list {
	padding: 0;
	margin-top: 15px;
	max-height: 0;
	overflow: hidden;
}

.news-list--active {
	max-height: 100%;
}

.news-list>li {
	list-style: none;
	padding: 20px;
	background-color: var(--tg-theme-secondary-bg-color);
	margin-bottom: 20px;
}
</style>