<!-- eslint-disable no-undef -->
<template>
    <div class="home">
        <div id="pano"></div>
        <button
            type="button"
            style="
                z-index: 99;
                width: 100px;
                height: 110px;
                background-color: red;
                position: absolute;
            "
            @click="load"
        >
            123
        </button>
    </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
const pano = ref(null);
onMounted(() => {
    // eslint-disable-next-line no-undef
    embedpano({
        swf: "./vtour/tour.swf",
        xml: "./vtour/tour.xml",
        target: "pano",
        html5: "auto",
        mobilescale: 1.0,
        passQueryParameters: true,
        onready: getPano,
    });
});
function getPano(params) {
    pano.value = params;
    // console.log(pano.value);
    // load();
}
function load() {
    // pano.value.call(
    //     "loadscene('AA', OPENBLEND(0.9, 0.0, 0.8, 0.9, easeOutQuad)"
    // );
    pano.value.call("addhotspot('a1')");
    pano.value.set("hotspot[a1].url", "/vtour/skin/vtourskin_hotspot.png");
    pano.value.set("hotspot['a1'].ath", -3.094);
    pano.value.set("hotspot['a1'].atv", 13.194);
    pano.value.set("hotspot['a1'].onclick", log);
    // pano.value.call(
    //     "set('hotspot[a1].url', './vtour/skin/vtourskin_hotspot.png')"
    // );
    // pano.value.call("set('hotspot[a1].ath', -3.094)");
    // pano.value.call("set('hotspot[a1].atv', 13.194)");
    // pano.value.set("hotspot['a1'].atv", 13.194);
    // pano.value.set("hotspot['a1'].distorted", false);
}
function log() {
    console.log("aaa");
    alert("hello world");
}
</script>

<style lang="scss">
.home {
    width: 100vw;
    height: 100vh;
    position: relative;
    #pano {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
    }
}
</style>
