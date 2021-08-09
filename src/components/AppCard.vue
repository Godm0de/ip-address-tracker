<template>
    <div class="card-wrapper">
        <div class="card">
            <div class="card__section">
                <h5 class="card__title">IP ADDRESS</h5>
                <p class="card__text">192.212.174.101</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">LOCATION</h5>
                <p class="card__text">Brooklyn, NY 10001</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">TIMEZONE</h5>
                <p class="card__text">UTC -05:00</p>
            </div>
            <div class="card__section">
                <h5 class="card__title">ISP</h5>
                <p class="card__text">SpaceX Starlink</p>
            </div>
        </div>
    </div>
</template>

<script>
module.exports = {
    name: 'card',
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
        font-weight: 700;
        font-size: 20px;
    }

    @media screen and (min-width: 769px) {
    }
}

.card-wrapper {
    padding: 0 1.33rem;
}
</style>
