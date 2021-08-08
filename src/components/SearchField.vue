<template>
    <div class="field container">
        <input type="text" class="field__input" v-model="inputTex" />
        <button @click="submitInput" class="field__submit">
            <img src="@/assets/images/icon-arrow.svg" alt="" />
        </button>
    </div>
</template>

<script>
module.exports = {
    name: 'search-field',
    data() {
        return {
            inputTex: '',
        };
    },
    methods: {
        submitInput() {
            return this.$emit('search', this.inputTex);
        },
    },
};
</script>

<style lang="scss" scoped>
.field {
    display: flex;
    max-width: 30.83rem;

    &__input {
        flex-grow: 1;
        padding: 1em 1.33em 1.06rem 1.33em;
        border: 0;
        border-radius: 0.83rem 0 0 0.83rem;

        &:focus {
            outline: 0;
        }

        &::placeholder {
            color: var(--grey-text-color);
        }
    }

    &__submit {
        background: var(--bg-button-color);
        border: 0;
        border-radius: 0 0.83rem 0.83rem 0;
        padding: 0 1.44rem;
        cursor: pointer;

        &:hover {
            background: var(--hover-button-color);
        }
    }
}
</style>
