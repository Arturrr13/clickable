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
        width: 217px;
        height: 111px;
        position: absolute;
        left: calc(50% - 108.5px);
        top: 12.5%;
        img{
            width: 100%;
        }
    }
    .bomb{
        position: absolute;
        right: -218px;
        top: -77px;
        max-width: 767px;
        width: 100%;
        animation: bombAnim 25s linear infinite;
        img{
            width: 100%;
        }
    }
    .candy{
        position: absolute;
        top: 47.1%;
        left: -160px;
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
        position: absolute;
        bottom: -31px;
        left: 9%;
        margin-right: 9%;
        max-width: 610px;
        max-height: 666px;
        img{
            width: 100%;
        }
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