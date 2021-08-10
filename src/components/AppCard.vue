<template>
    <div class="card-wrapper">
        <div class="card">
            <div class="card__section">
                <h5 class="card__title">IP ADDRESS</h5>
                <p class="card__text">{{ ip }}</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">LOCATION</h5>
                <p class="card__text">{{ location }}</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">TIMEZONE</h5>
                <p class="card__text">{{ timezone }}</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">ISP</h5>
                <p class="card__text">{{ isp }}</p>
            </div>
        </div>
    </div>
</template>

<script>
module.exports = {
    name: 'app-card',
    props: ['ip', 'location', 'timezone', 'isp'],
};
</script>

<style lang="scss" scoped>
.card {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 24px;
    text-align: center;
    background: var(--bg-card-color);
    margin: 1.33rem auto 0 auto;
    border-radius: 0.83rem;
    padding: 1.44rem 1.33rem 1.33rem 1.33rem;

    z-index: 1;
    max-width: 61.67rem;

    &__title {
        margin: 0;

        font-size: var(--fs-mobile-card-title);
        font-weight: 701;
        line-height: 12px;
        letter-spacing: 1.45833px;
        color: var(--grey-text-color);
    }

    &__text {
        margin: 0.39rem 0 0 0;
        font-weight: 500;
        font-size: 20px;
    }

    &__divider {
        display: none;

        width: 1px;
        height: 100%;
        color: var(--grey-text-color);
    }

    @media screen and (min-width: 1200px) {
        flex-direction: row;
        justify-content: space-between;
        gap: 32px;
        text-align: start;
        margin: 48px auto 0 auto;
        padding: 36px 32px 37px 32px;

        &__title {
            font-size: 12px;
        }

        &__text {
            font-size: 26px;
            width: 10ch;
        }

        &__section:not(:first-child) {
            border-left: 1px solid #979797;
            padding-left: 32px;
        }
    }
}

.card-wrapper {
    padding: 0 1.33rem;
}
</style>
