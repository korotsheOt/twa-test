<script setup>
const props = defineProps({
	firstname: String,
	username: String
})
</script>

<template>
	<div class="description">
		<h1 class="firstname">{{ firstname }}</h1>
		<p class="username">@{{ username }}</p>
	</div>
</template>

<style scoped>
.description {
	display: flex;
	flex-direction: column;
	gap: 10px;
}
.firstname {
	margin: 0;
	color: var(--tg-theme-text-color);
}

.username {
	margin: 0;
	color: var(--tg-theme-hint-color);
}
</style>