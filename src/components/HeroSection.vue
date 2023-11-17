<script setup lang="ts">
    const emit = defineEmits<{
        (e: 'setStatus', status: boolean): void
    }>()
</script>

<template>
    <div class="hero--section__wrapper">
        <div class="logo__wrapper">
            <img src="../assets/image/logo.png" alt="logo">
        </div>
        <div class="gift--text__wrapper">
            <span class="gift--text">
                Deposit 500, get 500 USDT<span class="gold--text"> as a gift</span>
            </span>
        </div>
        <div class="cashback--text__wrapper">
            <span>
                100% cashback for VIPs only
            </span>
        </div>
        <button 
            type="button" 
            class="become--vip"
            @click="emit('setStatus', true)"
        >
            Become a vip-player
        </button>
        <div class="diamond--1">
            <img src="../assets/image/Diamond.png" alt="diamond">
        </div>
        <div class="diamond--2">
            <img src="../assets/image/Diamond2.png" alt="diamond">
        </div>
        <div class="light--1">
            <img src="../assets/image/Light.png" alt="light">
        </div>
        <div class="light--2">
            <img src="../assets/image/Light.png" alt="light">
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .hero--section__wrapper{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        padding: 15.41% 0 0 23.125%;
        position: relative;
        overflow: hidden;
    }
    .gift--text__wrapper{
        max-width: 485px;
        margin: 54px 0;
        color: #FFF;
        font-size: 3.75em;
        font-style: normal;
        font-weight: 400;
        line-height: 1.2em;
        text-transform: uppercase;
        .gold--text{
            color: #EBBE7D;
            font-weight: 700;
        }
    }
    .cashback--text__wrapper{
        color:  #999;
        font-size: 1.5em;
        font-weight: 400;
        line-height: 1.33em;
        text-transform: uppercase;
    }
    .become--vip{
        margin-top: 101px;
        border-radius: 56px;
        background: #EBBE7D;
        padding: 15px 56px;
        backdrop-filter: blur(10px);
        border: none;
        color: #0B0B0A;
        font-size: 1.25em;
        font-weight: 700;
        line-height: 1.25em;
        text-transform: uppercase;
    }
    .diamond--1{
        position: absolute;
        top: 26%;
        left: -172px;
        animation: diamondAnim 4.5s linear infinite;
    }
    .diamond--2{
        position: absolute;
        bottom: 5%;
        right: 23%;
        animation: diamondAnim 4.5s linear infinite;
    }
    .light--1{
        position: absolute;
        bottom: 11.22%;
        right: 10.85%;
    }
    .light--2{
        position: absolute;
        top: 11%;
        right: 6%;
    }

    @keyframes diamondAnim {
	  	0% {
			filter: drop-shadow(0 0 0 rgb(255, 243, 178)); scale: (.9);
	  	}
	  	75% {
			filter: drop-shadow(11px 0px 14px rgb(255, 243, 178)); scale: (1.1);
	  	}
		100% {
			filter: drop-shadow(0 0 0 rgb(255, 243, 178)); scale: (.9);
	  	}
	}
</style>