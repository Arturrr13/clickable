<script setup lang="ts">
    import { onMounted, ref } from 'vue';
    import Input from '../UI/Input.vue';
    import Checkbox from '../UI/Checkbox.vue';

    const passwordValid = ref(false)
    const emailValid = ref(false)
    const checkboxValid = ref(false)

    onMounted(() => {
        const element = document.body.querySelector('.registration__wrapper') as HTMLDivElement
        window.scrollTo(0, document.body.scrollHeight/2 - element.clientHeight/2)
    })


    const sendForm = (e: Event) => {
        const element = e.target as HTMLInputElement
        const emailWrapper = element.children[1].children[0] as HTMLDivElement
        const passwordWrapper = element.children[2].children[0] as HTMLDivElement
        const email = emailWrapper.children[0] as HTMLInputElement
        const password = passwordWrapper.children[0] as HTMLInputElement
        console.log('email: ' + email.value + ';', 'password: ' + password.value + ';')
    }

    const getStatus = defineProps<{
        status: boolean
    }>()

    const emit = defineEmits<{
        (e: 'closePopup', status: boolean): void
    }>()

    const getInputStatus = (event: boolean, type: string) => type === 'email' ? emailValid.value = event : passwordValid.value = event
    const getCheckboxStatus = (event: boolean) => checkboxValid.value = event
</script>

<template>
    <div class="registration__wrapper" v-if="getStatus.status">
        <div class="game__wrapper">
            <div class="logo__wrapper">
                <img src="../../assets/image/logo.png" alt="logo">
            </div>
            <div class="gift--text__wrapper">
                <span class="gift--text">
                    Deposit 500,<br/> get 500 USDT as a gift
                </span>
            </div>
            <div class="cashback--text__wrapper">
                <span>
                    100% cashback for VIPs only
                </span>
            </div>
            <div class="image__wrapper">
                <div class="candy__wrapper--1">
                    <img src="../../assets/image/sweetBonanza/candy.png" alt="candy">
                </div>
                <div class="candy__wrapper--2">
                    <img src="../../assets/image/sweetBonanza/candy.png" alt="candy">
                </div>
                <div class="bomb__wrapper">
                    <img src="../../assets/image/sweetBonanza/bomb2.png" alt="bomb">
                </div>
                <div class="girl__wrapper">
                    <img src="../../assets/image/sweetBonanza/girl.png" alt="girl">
                </div>
                <div v-for="index of 5" :key="index" :class="`ellipse--${index}`"></div>
            </div>
        </div>
        <div class="from__wrapper">
            <div class="btn__wrapper">
                <button class="close__btn" @click="emit('closePopup', true)"></button>
            </div>
            <form action="#" method="post" @submit.prevent="sendForm">
                <h3>
                    Registration
                </h3>

                <Input type="email" @emailValid = "getInputStatus($event, 'email')" />
                <Input type="password" @passwordValid = "getInputStatus($event, 'password')" />

                <div class="checkbox__wrapper">
                    <checkbox @checkboxValid="getCheckboxStatus($event)"/>
                    <span>
                        By checking this box when registering on this site, the user confirms that he is over 18 years of age and has read, understood and accepted the 
                        <a href="#">Terms and Conditions.</a>
                    </span>
                </div>

                <button
                    class="create__btn"
                    :class="[passwordValid && emailValid && checkboxValid ? 'active' : '']"
                    type="submit"
                >
                    Create an account
                </button>
            </form>

            <span class="social__title">
                Or register with:
            </span>

            <div class="socials__wrapper">
                <div class="social__btn--Metamask" >
                    <img src="../../assets/image/social/Metamask.svg" alt="social">
                    <a href="https://metamask.io/" target="_blank" title="Metamask"></a>
                </div>
                <div class="social__btn--Apple" >
                    <img src="../../assets/image/social/Apple.svg" alt="social">
                    <a href="https://www.apple.com/"  target="_blank" title="Apple"></a>
                </div>
                <div class="social__btn--Facebook" >
                    <img src="../../assets/image/social/Facebook.svg" alt="social">
                    <a href="https://www.facebook.com/" target="_blank" title="Facebook"></a>
                </div>
                <div class="social__btn--Google" >
                    <img src="../../assets/image/social/Google.svg" alt="social">
                    <a href="https://www.google.com/" target="_blank" title="Google"></a>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .game__wrapper{
        background: $bkg-gradient;
        @include flex(normal, center, $direc: false);
        border-radius: 16px 0 0 16px;
    }
    .logo__wrapper{
        width: 142px;
        margin-top: 56px;
        img{
            width: 100%;
        }
    }
    .socials__wrapper{
        display: flex;
        gap: 8px;
        margin-top: 12px;
        div{
            border-radius: 8px;
            position: relative;
            background: #353535;
            padding: 8px;
            transition: all .25s ease;
            &:hover{
                box-shadow: 0px 0px 4px 1px #FCFCFC;
            }
        }
        a{
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 10;
        }
    }
    .ellipse--1{
        @include ellipse($text-gold, 108px, 75px, 142px, none, none, none, $pos: 't');
    }
    .ellipse--2{
        @include ellipse($text-gold, 85px, 60px, 152px, none, 50px, none, $pos: 'tr');
    }
    .ellipse--3{
        @include ellipse($text-gold, 108px, 75px, none, 122px, 0, none, $pos: 'br');
    }
    .ellipse--4{
        @include ellipse(#C20046, 224px, 102px, none, 55px, none, 74px, $pos: 'bl');
    }
    .ellipse--5{
        @include ellipse($text-gold, 108px, 75px, none, -53px, none, -20px, $pos: 'bl');
    }
    .image__wrapper{
        position: relative;
        overflow: hidden;
        height: 100%;
        width: 100%;
        border-radius: 0 0 0 16px;
    }
    .candy__wrapper--1{
        @include imageEl(75px, 66px, 8.8deg, 119px, none, none, 14px, $pos: 'tl');
    }
    .candy__wrapper--2{
        @include imageEl(105px, 92px, -67deg, none, -27px, none, 5px, $pos: 'bl');
    }
    .bomb__wrapper{
        @include imageEl(139px, 139px, -14.4deg, 32px, none, -42px, none, $pos: 'tr');
    }
    .girl__wrapper{
        @include imageEl(365px, 400px, 0, none, 0, none, 8px, $pos: 'bl');
    }
    .gift--text{
        @include text(1em, $text-white, 1em, 400, 0.32px, $ff: false, $tt: true);
    }
    .gift--text__wrapper{
        text-align: center;
        margin: 47px 0 8px 0;
    }
    .cashback--text__wrapper span{
        @include text(1em, $text-gold, 1em, 400, 0.32px, $ff: false, $tt: true);
    }
    .registration__wrapper{
        position: absolute;
        display: grid;
        grid-template-columns: 1fr 1fr;
        border-radius: 16px;
        background: #131313; 
        box-shadow: 0px 4px 24px 0px rgba(21, 19, 14, 0.64);
        max-width: 720px;
        max-height: 704px;
        width: 100%;
        height: 100%;
    }
    .from__wrapper{
        @include flex(normal, center, $direc: false);
        padding: 16px;
    }
    .btn__wrapper{
        width: 100%;
        @include flex(flex-end, normal, $direc: true);
    }
    .close__btn{
        width: 40px;
        height: 40px;
        background: #202020;
        border-radius: 10px;
        border: none;
        padding-top: 3px;
        transition: all .25s ease;
        &:hover{
            box-shadow: 0px 0px 4px 1px #FCFCFC;
        }
        &::after{
            content: url(../../assets/image/svg/CloseBtn.svg);
        }
    }

    form{
        @include flex(normal, center, $direc: false);
    }

    h3{
        @include text(1.2em, $text-white, 1.25em, 400, 0.4px, $ff: false, $tt: false);
        margin: 48px 0;
    }
    .checkbox__wrapper{
        display: flex;
        span{
            @include text(1.2em, $text-grey, .625em, 400, 0.2px, $ff: false, $tt: false);
            margin-left: 8px;
            a{
                color: #E4C086;
            }
        }
    }
    .create__btn{
        @include button($btn-locked, 16px, 16px, 10px);
        @include text(1em, #282828, .875em, 400, 0.28px, $ff: false, $tt: false);
        width: 100%;
        margin-top: 32px;
        cursor: not-allowed;
        &.active{
            background: $btn-gold;
            cursor: pointer;
            &:hover{
                background: $btn-hover;
            }
        }
    }
    .social__title{
        @include text(1.33em, $text-white, .75em, 400, 0.36px, $ff: false, $tt: false);
        margin-top: 32px;
    }
</style>