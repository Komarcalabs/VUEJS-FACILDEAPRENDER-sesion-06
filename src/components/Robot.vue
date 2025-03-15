<script setup>
const { top, left } = defineProps({
    top: Number,
    left: Number
})

const isActive = defineModel({ default: false })

</script>
<template>
    <div id="robot" :style="{ top: top + 'px', left: left + 'px' }">
        <button class="button-on-off" @click="isActive = !isActive"
            :class="{ 'button-on': isActive, 'button-off': !isActive }">
            <span v-if="isActive">ON</span>
            <span v-else>OFF</span>
        </button>
        <img class="image-robot" src="@/assets/robot.svg" alt="robot" :class="{ 'image-off': !isActive }">
    </div>
</template>
<style scoped>
#robot {
    position: absolute;
    transition: all ease-in 250ms;
}

.button-on-off {
    padding: 4px 8px;
    border-radius: 10px;
    margin: 1rem auto;
}

.image-robot {
    display: block;
    height: 50px;
    width: auto;
}

.button-on {
    background-color: red;
    color: white;
    font-weight: bold;
}

.button-off {
    background-color: lightgray;
    color: black;
    font-weight: bold;
}

.image-off {
    filter: grayscale()
}
</style>