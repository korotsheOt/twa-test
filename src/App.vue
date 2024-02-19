<script setup>
import { onMounted, ref } from "vue"
import Profile from "./components/Profile.vue";
import NewsList from "./components/NewsList.vue";
import axios from "axios";

const telegramApp = window.Telegram.WebApp;
const user = telegramApp.initDataUnsafe.user;

const firstname = ref('');
const username = ref('');
const photo = ref('');
const newsData = ref('');

onMounted(() => {
	telegramApp.ready();
	telegramApp.expand();

	firstname.value = user.first_name;
	username.value = user.username;
	photo.value = user.photo_url;
});

onMounted(() => {
	axios
		.get('https://twa-test-back.onrender.com/')
		.then((response) => {
			newsData.value = response.data;
		})
		.catch((error) => {
			console.log(error.message);
		});
})
</script>

<template>
	<Profile :firstname="firstname" :username="username" :photo="photo" />
	<NewsList :data="newsData" />
</template>