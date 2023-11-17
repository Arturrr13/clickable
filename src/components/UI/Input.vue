<script setup lang="ts">
    const emit = defineEmits<{
        (e: 'emailValid', status: boolean): void,
        (e: 'passwordValid', status: boolean): void
    }>()

    const getType = defineProps<{
        type: string
    }>()

    const activeIn = (e: Event) => {
        const element = e.target as HTMLInputElement
        const elementParent = element.parentElement as HTMLDivElement
        elementParent.classList.add('active')
    }

    const closeIn = (e: Event) => {
        const element = e.target as HTMLInputElement
        const elementParent = element.parentElement as HTMLDivElement
        elementParent.classList.remove('active')
        if(element.value.length > 0) checkInput(element, elementParent)
    }

    const checkInput = (input: HTMLInputElement, wrapper: HTMLDivElement) => {
        const err = (status: boolean) => {
            if(status){
                wrapper.classList.add('active__error')
                wrapper.classList.add('active')
            } else {
                wrapper.classList.remove('active__error')
                wrapper.classList.remove('active')
            }
        }

        const checkEmail = () => {
            if(input.value.length > 0 && Boolean(input.value.match(/^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/)) !== false) {
                err(false)
                emit('emailValid', true)
                wrapper.classList.add('active')
            } else {
                err(true)
                emit('emailValid', false)
            }
        }

        const checkPassword = () => {
            if(input.value.length > 5 ) {
                err(false)
                emit('passwordValid', true)
                wrapper.classList.add('active')
            } else {
                err(true)
                emit('passwordValid', false)
            }
        }

        input.type === 'email' ? checkEmail() : checkPassword()

    }
</script>

<template>
    <div style="width: 100%;">
        <div class="input--email__wrapper" v-if="getType.type === 'email'">
            <input 
                type="email"
                name="email"
                placeholder="Email"
                @click="activeIn"
                @blur="closeIn"
            >
            <span class="input__error">
                Provide a valid e-mail address
            </span>
        </div>
    
        <div class="input--password__wrapper" v-if="getType.type === 'password'">
            <input 
                type="password"
                name="password"
                placeholder="Password"
                @click="activeIn"
                @blur="closeIn"
            >
            <span class="input__error">
                Provide a valid password
            </span>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    input[type=email],
    input[type=password]{
        border-radius: 8px;
        outline: none;
        border: 1px solid #353535;
        background: #131313;
        padding: 16px 16px 16px 40px;
        width: 100%;
        transition: all .25s ease;
        color: #FCFCFC;
        font-family: 'Stolzl';
        font-size: .825em;
        line-height: 1.1em;
        letter-spacing: 0.28px;
        &::placeholder{
            color: #999;
            font-family: 'Stolzl';
            font-size: .875em;
            letter-spacing: 0.28px;
        }
        &:hover{
            border: 1px solid #FCFCFC;
        }
        &:focus{
            border: 1px solid #FCFCFC;
        }
    }

    .input--email__wrapper,
    .input--password__wrapper{
        display: flex;
        position: relative;
        align-items: center;
        width: 100%;
        &::before{
            position: absolute;
            left: 16px;
        }
        &::after{
            content: none;
        }
        .input__error{
            display: none;
        }
        &.active{
            input[type=email]::placeholder,
            input[type=password]::placeholder{
                color: #99999900;
            }
            &::after{
                position: absolute;
                top: -6px;
                left: 20px;
                background: #131313;
                padding: 0 4px;
                color: #999;
                font-family: 'Stolzl';
                font-size: .625em;
                letter-spacing: 0.2px;
            }
        }
        &.active__error{
            input[type=email],
            input[type=password]{
                border: 1px solid #FD4646;
            }
            .input__error{
                display: block;
                position: absolute;
                bottom: -7px;
                right: 12px;
                padding: 0 4px;
                color: #FD4646;
                background: #131313;
                font-family: 'Stolzl';
                font-size: .625em;
                line-height: 1.6em;
                letter-spacing: 0.2px;
            }
        }
    }
    .input--email__wrapper{
        &::before{
            content: url(../../assets/image/svg/Mail.svg);
        }
        &.active::after{
            content: 'Email';
        }
    }
    .input--password__wrapper{
        margin: 24px 0 32px 0;
        &::before{
            content: url(../../assets/image/svg/Password.svg);
            top: 18px;
        }
        &.active::after{
            content: 'Password';
        }
    }
</style>