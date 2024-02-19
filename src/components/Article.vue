<script setup>
const props = defineProps({
	title: String,
	description: String,
	image: String,
})

</script>

<template>
	<div class="article">
		<div class="image-block">
			<img :src="image" alt="Article image">
		</div>
		<div class="text-block">
			<p class="title">{{ title }}</p>
			<p class="description">{{ description }}</p>
		</div>
	</div>
</template>

<style scoped>
.article { 
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-between;
	gap: 15px;
	width: 100%;
	color: var(--tg-theme-text-color);
}
.image-block {
	max-width: 35%;
}

.image-block img {
	width: 100%;
	object-fit: cover;
	border-radius: 10px;
	border: 2px solid var(--tg-theme-text-color);
}

.title {
	font-size: 20px;
    font-weight: 600;
	margin: 5px 0;
}

@media screen and (max-width: 768px) {
	.article { 
		flex-direction: column;
	}

	.image-block {
		max-width: 100%;
	}
}
</style>