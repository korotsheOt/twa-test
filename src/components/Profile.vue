<script setup>
import Description from './Description.vue';
import Avatar from './Avatar.vue';
import { ref, watchEffect } from 'vue';

const props = defineProps({
	firstname: String,
	username: String,
	photo: String,
})

const nameFirstLetter = ref('');

watchEffect(()=> {
	nameFirstLetter.value = props.firstname && props.firstname !== "" ? props.firstname.slice(0,1).toUpperCase() : "A";
})

</script>

<template>
	<div class="profile">
		<Avatar :nameFirstLetter="nameFirstLetter" :photo="photo"/>
		<Description :firstname="firstname" :username="username"/>
	</div>
</template>

<style scoped>
.profile {
	display: flex;
	flex-direction: row;
	align-items: flex-start;
	gap: 20px;
	max-width: 100%;
	padding: 15px;
	margin-bottom: 20px;
	background-color: var(--tg-theme-secondary-bg-color);
}
</style>