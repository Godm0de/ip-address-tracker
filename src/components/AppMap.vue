<template>
    <GmapMap :center="center" :zoom="19" map-type-id="terrain" class="map">
        <GmapMarker :position="center" :clickable="false" :draggable="false" />
    </GmapMap>
</template>

<script>
module.exports = {
    name: 'app-map',
    props: {
        center: {
            lat: {
                type: Number,
                default: 10,
            },
            lng: {
                type: Number,
                default: 10,
            },
        },
    },
};
</script>

<style lang="scss" scoped>
.map {
    height: calc(100vh - 300px);

    @media screen and (min-width: 1200px) {
        height: calc(100vh - 280px);
    }
}
</style>
