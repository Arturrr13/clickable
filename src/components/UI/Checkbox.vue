<script setup lang="ts">
    const emit = defineEmits<{
        (e: 'checkboxValid', status: boolean): void
    }>()

    const activeCheckbox = (e: Event) => {
        const element = e.target as HTMLInputElement
        const elementParent = element.parentElement as HTMLDivElement
        console.log(element.checked)
        if(element.checked){
            elementParent.classList.remove('active')
            emit('checkboxValid', false)
        } else {
            elementParent.classList.add('active')
            emit('checkboxValid', true)
        }
    }
</script>

<template>
    <div class="container">
        <input type="checkbox" checked @click="activeCheckbox"> 
    </div>
</template>

<style lang="scss" scoped>
    input[type=checkbox]{
        position: absolute;
        opacity: 0;
        width: 18px;
        height: 18px;
        &:hover{
            cursor: pointer;
        }
    }
    .container{
        min-width: 18px;
        height: 18px;
        border-radius: 2px;
        border: 1px solid #999;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all .25s ease;
        &:hover{
            border: 1px solid #FCFCFC;
        }
        &.active{
            background: #E4C086;
            border: none;
            &::after{
                content: url(../../assets/image/svg/CheckBox.svg);
            }
            &:hover{
                border: none;
            }
        }
    }
</style>