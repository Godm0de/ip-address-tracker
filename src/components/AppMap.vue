<template>
    <GmapMap :center="{ lat: 10, lng: 10 }" :zoom="7" map-type-id="terrain" class="map"></GmapMap>
</template>

<script></script>

<style lang="scss" scoped>
.map {
    height: calc(100vh - 300px);
}
</style>
