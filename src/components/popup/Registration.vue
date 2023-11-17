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
                <div class="ellipse--1"></div>
                <div class="ellipse--2"></div>
                <div class="ellipse--3"></div>
                <div class="ellipse--4"></div>
                <div class="ellipse--5"></div>
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
        background: linear-gradient(180deg, #130625 0%, #1B0929 100%);
        display: flex;
        flex-direction: column;
        align-items: center;
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
        width: 108px;
        height: 108px;
        border-radius: 50%;
        background: #EBBE7D;
        filter: blur(75px);
        position: absolute;
        top: 142px;
    }
    .ellipse--2{
        width: 85px;
        height: 85px;   
        border-radius: 50%;
        background: #EBBE7D;
        filter: blur(59.02778244018555px);
        position: absolute;
        top: 152px;
        right: 50px;
    }
    .ellipse--3{
        width: 108px;
        height: 108px;
        border-radius: 50%;
        background: #EBBE7D;
        filter: blur(75px);
        position: absolute;
        right: 0;
        bottom: 122px;
    }
    .ellipse--4{
        width: 224px;
        height: 224px;
        border-radius: 50%;
        background: #C20046;
        filter: blur(102.16216278076172px);
        position: absolute;
        bottom: 55px;
        left: 74px;
    }
    .ellipse--5{
        width: 108px;
        height: 108px;
        border-radius: 50%;
        background: #EBBE7D;
        filter: blur(75px);
        position: absolute;
        bottom: -53px;
        left: -20px;
    }
    .image__wrapper{
        position: relative;
        overflow: hidden;
        height: 100%;
        width: 100%;
        border-radius: 0 0 0 16px;
    }
    .candy__wrapper--1{
        max-width: 75.892px;
        max-height: 66.026px;
        transform: rotate(8.779deg);
        position: absolute;
        top: 119px;
        left: 14px;
        z-index: 1;
        img{
            width: 100%;
        }
    }
    .candy__wrapper--2{
        max-width: 105.691px;
        max-height: 91.951px;
        transform: rotate(-67deg);
        position: absolute;
        bottom: -27px;
        left: 5px;
        z-index: 1;
        img{
            width: 100%;
        }
    }
    .bomb__wrapper{
        max-width: 138.923px;
        max-height: 138.923px;
        position: absolute;
        top: 32px;
        transform: rotate(-14.343deg);
        right: -42px;
        z-index: 1;
        img{
            width: 100%;
        }
    }
    .girl__wrapper{
        position: absolute;
        max-width: 365px;
        max-height: 399.006px;
        bottom: 0;
        left: 8px;
        position: absolute;
        z-index: 1;
        img{
            width: 100%;
        }
    }
    .gift--text{
        color: #FCFCFC;
        font-family: 'Stolzl';
        font-size: 1em;
        line-height: 1em;
        letter-spacing: 0.32px;
        text-transform: uppercase;
    }
    .gift--text__wrapper{
        text-align: center;
        margin: 47px 0 8px 0;
    }
    .cashback--text__wrapper span{
        color: #E4C086;
        font-family: 'Stolzl';
        font-size: 1em;
        line-height: 1em;
        letter-spacing: 0.32px;
        text-transform: uppercase;
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
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 16px;
    }
    .btn__wrapper{
        width: 100%;
        display: flex;
        justify-content: flex-end;
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
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    h3{
        color: #FCFCFC;
        font-family: 'Stolzl';
        font-size: 1.25em;
        font-weight: 400;
        line-height: 1.2em;
        letter-spacing: 0.4px;
        margin: 48px 0;
    }
    .checkbox__wrapper{
        display: flex;
        span{
            color: #999;
            font-family: 'Stolzl';
            font-size: .625em;
            line-height: 1.2em;
            letter-spacing: 0.2px;
            margin-left: 8px;
            a{
                color: #E4C086;
            }
        }
    }
    .create__btn{
        border-radius: 10px;
        border: none;
        background: #1C1C1C;
        padding: 16px;
        color: #282828;
        font-family: 'Stolzl';
        font-size: .875em;
        letter-spacing: 0.28px;
        width: 100%;
        margin-top: 32px;
        cursor: not-allowed;
        &.active{
            background: #E4C086;
            cursor: pointer;
            &:hover{
                background: #FCFCFC;
            }
        }
    }
    .social__title{
        color: #FCFCFC;
        font-family: 'Stolzl';
        font-size: .75em;
        line-height: 1.33em;
        letter-spacing: 0.36px;
        margin-top: 32px;
    }
</style>