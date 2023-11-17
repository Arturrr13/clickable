<script setup lang="ts">
	import HeroSection from './components/HeroSection.vue';
	import BonanzaSection from './components/BonanzaSection.vue';
	import Registration from './components/popup/Registration.vue';
	import { ref } from 'vue';

	const status = ref(false)
	const popupStatus = ref(false)

	const openRegistration = (event: boolean) => { 
		status.value = event
		popupStatus.value = !event
	}
	const closeRegistration = (event: boolean) => popupStatus.value = event
</script>

<template>
	<main>
		<hero-section @setStatus="openRegistration($event)"/>
		<bonanza-section />
		<div class="popup__wrapper" v-if="status && !popupStatus">
			<registration :status="status" @closePopup="closeRegistration($event)"/>
		</div>

		<div class="chip__wrapper">
			<img src="./assets/image/Chip.png" alt="chip poker">
		</div>
	</main>
</template>

<style lang="scss">
	main{
		height: 100vh;
		display: grid;
    	grid-template-columns: 1fr 1fr;
		overflow: hidden;
		position: relative;
	}
	.popup__wrapper{
		background: rgba(0, 0, 0, 0.70);
		backdrop-filter: blur(7.5px);
		position: absolute;
		width: 100%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 10;
	}
	.chip__wrapper{
		position: absolute;
    	top: -7.5%;
    	left: 44.15%;
		animation: chipAnim 4.5s linear infinite;
	}

	@keyframes chipAnim {
	  	0% {
			transform: rotate3d(0, 0, 0, 0deg);
	  	}
	  	75% {
			transform: rotate3d(1, 6, 6, 35deg);
	  	}
		100% {
			transform: rotate3d(0, 0, 0, 0deg);
	  	}
	}
</style>

