<template>
    <div class="alert-wrapper">
        <span class="alert">
            <slot></slot>
            <span class="alert__close" @click="emitClose" />
        </span>
    </div>
</template>

<script>
module.exports = {
    name: 'app-alert',
    methods: {
        emitClose() {
            this.visible = false;
            this.$emit('close');
        },
    },
};
</script>

<style lang="scss" scoped>
.alert {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
    max-width: min(100%, 30.83rem);
    padding: 1rem;
    border-radius: 5px;
    color: #721c24;
    background-color: #f8d7da;
    border-color: #f5c6cb;
    font-size: 18px;

    &-wrapper {
        position: fixed;
        bottom: 0;
        margin-bottom: 1rem;
        width: 100%;
    }

    &__close {
        background: url('~@/assets/images/close.svg');
        background-size: 16px 16px;
        background-repeat: no-repeat;
        background-position: center;
        width: 16px;
        height: 16px;
        cursor: pointer;
        padding: 12px;
        border-radius: 5px;
        transition: background-color 0.2s linear;
    }

    &__close:hover {
        background-color: darken(#f5c6cb, 5%);
    }
}
</style>
