<template>
    <div id="app">
        <header class="header">
            <h1 class="header__title">IP Address Tracker</h1>
            <app-search-field></app-search-field>
            <app-card></app-card>
        </header>
        <main>
            <app-map></app-map>
        </main>
    </div>
</template>

<script>
import AppSearchField from './components/AppSearchField.vue';
import AppMap from './components/AppMap.vue';
import AppCard from './components/AppCard.vue';

export default {
    name: 'App',
    components: {
        AppCard,
        AppMap,
        AppSearchField,
    },
};
</script>

<style lang="scss">
@use "./assets/scss/index.scss";

.header {
    background: url('~@/assets/images/pattern-bg.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    max-height: 300px;

    &__title {
        margin: 0;
        text-align: center;
        padding: 1.44rem 0 1.61rem 0;
        font-size: var(--fs-mobile-heading);
        font-weight: 500;
        color: var(--light-text-color);
    }

    @media screen and (min-width: 1200px) {
        max-height: 280px;

        &__title {
            padding: 33px 0 31px 0;
            font-size: 32px;
        }
    }
}
</style>
