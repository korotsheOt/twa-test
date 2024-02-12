<script setup>
const props = defineProps({
	photo: String,
	nameFirstLetter: String
})
</script>

<template>
	<div class="avatar">
		<img v-if="photo" class="photo" :src="photo" alt="Profile photo" />
		<p v-else class="avatar-letter">{{nameFirstLetter}}</p>	
	</div>
</template>

<style scoped>
.avatar {
	width: 100px;
	height: 100px;
	background-color: #d6c2a8;
	border: 2px solid var(--tg-theme-text-color);
    border-radius: 10px;
}
.photo {
	width: 100%;
	height: 100%;
	object-fit: cover;
	border-radius: 10px;
}

.avatar-letter {
	display: flex;
    width: 100%;
    height: 100%;
    margin: 0;
    font-size: 40px;
    align-items: center;
    justify-content: center;
}
</style>