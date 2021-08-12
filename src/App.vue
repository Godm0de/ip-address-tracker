<template>
    <div id="app">
        <header class="header">
            <h1 class="header__title">IP Address Tracker</h1>
            <app-search-field @search="searchIpAddress" :disabled="disabled"></app-search-field>
            <app-card :ip="ip" :location="location" :timezone="timezone" :isp="isp"></app-card>
        </header>
        <main>
            <app-map :center="{ lat: lat, lng: lng }"></app-map>
            <transition name="fade">
                <app-alert v-show="error" @close="resetError">The IP v4 or v6 is invalid! Please check the (RFC791)</app-alert>
            </transition>
        </main>
    </div>
</template>

<script>
import axios from 'axios';
import AppSearchField from './components/AppSearchField.vue';
import AppMap from './components/AppMap.vue';
import AppCard from './components/AppCard.vue';
import AppAlert from './components/AppAlert.vue';

export default {
    name: 'App',
    components: {
        AppCard,
        AppMap,
        AppSearchField,
        AppAlert,
    },
    data() {
        return {
            ip: '',
            location: '',
            timezone: '',
            isp: '',
            error: false,
            lat: 0,
            lng: 0,
            disabled: false,
        };
    },
    mounted() {
        this.searchIpAddress('');
    },
    methods: {
        searchIpAddress(ip) {
            this.disabled = true;
            const ipProp = ip || '';
            axios
                .get(`https://geo.ipify.org/api/v1?apiKey=${process.env.VUE_APP_GEO_IPIFY_KEY}&ipAddress=${ipProp}`)
                .then((response) => {
                    const info = response.data;
                    this.ip = info.ip;
                    this.location = `${info.location.city}, ${this.createAcronym(info.location.region)} ${info.location.postalCode}`;
                    this.timezone = `UTC ${info.location.timezone}`;
                    this.isp = info.isp;
                    this.lat = info.location.lat;
                    this.lng = info.location.lng;
                    this.disabled = false;
                })
                .catch(() => {
                    this.disabled = false;
                    this.error = true;
                });
        },
        createAcronym(phrase) {
            const words = phrase.split(/\s|-/);
            return words.length > 1
                ? words
                      .map((value) => value.charAt(0))
                      .join('')
                      .toUpperCase()
                : words[0]
                      .split('')
                      .filter((char) => !['a', 'e', 'i', 'o', 'u'].includes(char))
                      .splice(0, 2)
                      .join('')
                      .toUpperCase();
        },
        resetError() {
            this.error = false;
        },
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

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>
