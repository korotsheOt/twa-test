<script setup>
import { onMounted, ref } from 'vue'
import Profile from "./components/Profile.vue";

const telegramApp =	window.Telegram.WebApp;
const user = telegramApp.initDataUnsafe.user;

const firstname = ref('');
const username = ref('');
const photo = ref('');

onMounted(() => {
	telegramApp.ready();
	telegramApp.expand();

	firstname.value = user.first_name;
	username.value = user.username;
	photo.value = user.photo_url;

	setTimeout(()=> {
		telegramApp.MainButton.setText("That's all. Close app");
		telegramApp.MainButton.onClick(() => {
			telegramApp.close();
		});
		telegramApp.MainButton.show();
	}, 3000)
})
</script>

<template>
	<Profile 
		:firstname="firstname"
		:username="username"
		:photo="photo"/>
</template>
