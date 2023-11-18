<template>
    <div class="bonanza--section__wrapper">
        <div class="bonanza__wrapper">
            <div class="logo">
                <img src="../assets/image/sweetBonanza/logo.png" alt="logo">
            </div>
            <div class="bomb">
                <img src="../assets/image/sweetBonanza/bomb2.png" alt="bomb">
            </div>
            <div class="girl">
                <img src="../assets/image/sweetBonanza/girl.png" alt="girl">
            </div>
        </div>
        <div class="candy">
            <img src="../assets/image/sweetBonanza/candy.png" alt="candy">
        </div>
    </div>
    
</template>

<style lang="scss" scoped>
    .bonanza--section__wrapper{
        background: url(../assets/image/background/bkg_sweetBonanza.jpg);
        background-size: 100% 100%;
        max-height: 100vh;
        position: relative;
    }
    .bonanza__wrapper{
        position: relative;
        overflow: hidden;
        height: 100%;
    }
    .logo{
        @include bonanzaEl(217px, 111px, 12.5%, none, none, calc(50% - 108.5px), $pos: 'tl');
        width: 100%;
    }
    .bomb{
        @include bonanzaEl(767px, 767px, -77px, none, -218px, none, $pos: 'tr');
        animation: bombAnim 25s linear infinite;
    }
    .candy{
        @include bonanzaEl(250px, 250px, 47.1%, none, none, -160px, $pos: 'tl');
        animation: candyAnim 75s linear infinite;
        &:hover{
            transition: all 1s ease;
            scale: 1.1;
            filter: hue-rotate(60deg);
        }
        img{
            transform: rotate(8.779deg);
        }
    }
    .girl{
        @include bonanzaEl(610px, 666px, none, -31px, none, 9%, $pos: 'bl');
    }

    @keyframes bombAnim {
	  	0% {
			transform: translateX(100%); transform: translateY(-100%);
	  	}
	  	4% {
			transform: translateY(0);
	  	}
        5% {
			transform: translateY(-12%);
	  	}
        6% {
			transform: translateY(0);
	  	}
        7% {
			transform: translateY(-8%);
	  	}
        8% {
			transform: translateY(0);
	  	}
        9% {
			transform: translateY(-4%);
	  	}
        10% {
			transform: translateY(0);
	  	}
        83%{
            transform: translateX(0); transform: translateY(0);
        }
        85%{
            transform: translateX(100%);
        }
		100% {
			transform: translateX(100%); transform: translateY(-100%);
	  	}
	}

    @keyframes candyAnim {
	  	0% {
			transform: rotate(0deg);
	  	}
	  	15% {
			transform: rotate(360deg);
	  	}
        85%{
            transform: rotate(360deg);
        }
		100% {
			transform: rotate(0deg);
	  	}
	}
</style>