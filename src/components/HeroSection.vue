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
        @include text(1.2em, #FFF, 3.75em, 400, 0, $ff: true, $tt: true);
        max-width: 485px;
        margin: 54px 0;
        .gold--text{
            color: $text-gold;
            font-weight: 700;
        }
    }
    .cashback--text__wrapper{
        @include text(1.33em, $text-grey, 1.5em, 400, normal, $ff: true, $tt: true);
    }
    .become--vip{
        @include button($btn-gold, 15px, 56px, 56px);
        z-index: 1;
        margin-top: 101px;
        backdrop-filter: blur(10px);
        color: #0B0B0A;
        font-size: 1.25em;
        font-weight: 700;
        line-height: 1.25em;
        text-transform: uppercase;
        &:hover{
            box-shadow: inset 0 60px 0 0 $btn-hover;
        }
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
        animation: lightAnim 3.5s linear infinite;
    }
    .light--2{
        position: absolute;
        top: 11%;
        right: 6%;
        animation: lightAnim 2.5s linear infinite;
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

    @keyframes lightAnim {
	  	0% {
            opacity: 0;
	  	}
        75% {
			opacity: 1;
	  	}
		100% {
			opacity: 0;
	  	}
	}
</style>