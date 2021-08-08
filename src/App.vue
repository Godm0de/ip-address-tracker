<template>
    <div id="app">
        <header class="header">
            <h1 class="header__title">IP Address Tracker</h1>
            <search-field></search-field>
            <card></card>
        </header>
        <main>
            <map></map>
        </main>
    </div>
</template>

<script>
import SearchField from './components/SearchField.vue';
import Card from './components/Card.vue';

export default {
    name: 'App',
    components: {
        SearchField,
        Card,
    },
};
</script>

<style lang="scss">
@use "./assets/scss/index.scss";

.header {
    background: url('~@/assets/images/pattern-bg.png');
    background-size: cover;
    max-height: 20.83rem;

    &__title {
        margin: 0;
        text-align: center;
        padding: 1.44rem 0 1.61rem 0;
        font-size: var(--fs-mobile-heading);
        color: var(--light-text-color);
    }
}
</style>
