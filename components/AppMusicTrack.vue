<template>
    <div 
        class="main-track" 
        @mousedown="handleMouseDown"
        @mouseup="handleMouseUp"
        @mousemove="handleMouseMove"
    >
        <label :for="inputId" class="visually-hidden">
            Track
        </label>
        <input 
            :id="inputId"
            ref="inputElement"
            type="range" 
            min="0" 
            max="100"
            value="0"
        />
        <div class="range-visual">
            <span class="range-visual-thumb"/>
        </div>
    </div>
</template>

<script setup>
const props = defineProps({
    inputId: {
        type: String,
        required: true
    }
})

const { inputId } = toRefs(props)

const percentage = ref(0)

const isDragging = ref(false)
function handleMouseDown() {
    isDragging.value = true
}

const inputElement = ref(null)
function handleMouseUp() {
    isDragging.value = false
    updatePercentage(event.clientX)
}

function handleMouseMove(event) {
    if(!isDragging.value) return
    updatePercentage()
}

function updatePercentage() {
    percentage.value = inputElement.value.value + '%'
}
</script>

<style lang="scss" scoped>
.main-track {
    position: relative;
    width: 100%;
    input {
        opacity: 0;
        position: absolute;
        left: 0;
        z-index: 1;
    }

    .range-visual {
        position: relative;
        height: 20px;
        width: 100%;
        &:before {
            content: '';
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            height: 2px;
            width: v-bind(percentage);
            border-radius: 50px;
            background-color: $text_color;
        }
        &:after {
            content: '';
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            height: 2px;
            width: 100%;
            border-radius: 50px;
            background-color: rgba($text_color, 0.4);
        }
        &-thumb {
            background-color: $text_color;
            width: 12px;
            aspect-ratio: 1;
            border-radius: 50%;
            position: absolute;
            left: v-bind(percentage);
            top: 0;
            transform: translateY(calc(-50% + 10px));
            box-shadow: 0 0 4px 2px rgba($text_color, 0.8);
        }
    }
}
</style>