<script setup>
import leftArrow from './Icon/leftArrow.vue'
import topArrow from './Icon/topArrow.vue'
import rightArrow from './Icon/rightArrow.vue'
import bottomArrow from './Icon/bottomArrow.vue'

const { isRobotActive } = defineProps(["isRobotActive"])

const x = defineModel("x", {
    default: 0
})
const y = defineModel("y", {
    default: 0
})

function moveY(value) {
    y.value += value
}

function moveX(value) {
    x.value += value
}

</script>
<template>
    <div id="control">
        <div class="control-indicator">
            <div class="led led-on" v-if="isRobotActive"></div>
            <div class="led led-off" v-else></div>
        </div>
        <div class="control-movimiento">
            <button class="control-movimiento__button control-movimiento__button--up" :disabled="!isRobotActive"
                @click="moveY(-10)">
                <topArrow></topArrow>
            </button>
            <button class="control-movimiento__button control-movimiento__button--bottom" :disabled="!isRobotActive"
                @click="moveY(10)">
                <bottomArrow></bottomArrow>
            </button>
            <button class="control-movimiento__button control-movimiento__button--left" :disabled="!isRobotActive"
                @click="moveX(-10)">
                <leftArrow></leftArrow>
            </button>
            <button class="control-movimiento__button control-movimiento__button--right" :disabled="!isRobotActive"
                @click="moveX(10)">
                <rightArrow></rightArrow>
            </button>
        </div>
    </div>
</template>
<style scoped>
.control-movimiento {
    position: relative;
    width: 150px;
    height: 150px;
    border: thin solid lightgray;
    border-radius: 10px;
    padding: 0.25rem;
}

.control-movimiento__button {
    position: absolute;
    background-color: lightblue;
    color: black;
    border: thin solid black;
    border-radius: 50%;
    font-size: 2em;
    padding: 0.25rem;
    transition: all 100ms;
}

.control-movimiento__button:active {
    background-color: aqua;
    color: red
}

.control-movimiento__button:disabled {
    background-color: gray;
    color: black
}

.control-movimiento__button--up {
    top: 0px;
    right: 50%;
    transform: translateX(+50%);
}

.control-movimiento__button--bottom {
    bottom: 0px;
    right: 50%;
    transform: translateX(+50%);
}

.control-movimiento__button--left {
    top: 50%;
    left: 0px;
    transform: translateY(-50%);
}

.control-movimiento__button--right {
    top: 50%;
    right: 0px;
    transform: translateY(-50%);
}

.control-indicator {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 150px;
    height: 25px;
    border: thin solid lightgray;
    border-radius: 10px;
}

.led {
    height: 10px;
    width: 10px;
    border-radius: 10px;
}

.led-on {
    background-color: red;
}

.led-off {
    background-color: gray;
}
</style>