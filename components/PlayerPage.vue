<template>
    <section class="player" :class="{ active: active }">
        <BlobBackground/>
        <div class="player-content">
            <header class="header">
                <label for="search-input" class="visually-hidden">
                    Search for songs or artists
                </label>
                <span class="search-wrapper">
                    <Icon name="ph:magnifying-glass"/>
                    <input 
                        id="search-input" 
                        type="search" 
                        placeholder="Search for songs or artists"
                    />
                </span>
                <AppButton class="icon danger" @click="emits('close:player')">
                    <span class="visually-hidden"></span>
                    <Icon name="ph:x-circle"/>
                </AppButton>
            </header>
            <section class="genres">
                <h2 class=section-title>
                    Find the perfect match to your taste
                </h2>
                <div ref="genresContainerElement" class="genres-container">
                    <ul class="genres-listing">
                        <li
                            v-for="genre in genres" :key="genre.id"
                            class="genres-listing-item"
                            ref="genresElements"
                        >
                            <button 
                                class="genres-listing-item-button" 
                                :class="genre.name.toLowerCase()"
                            >
                                <span class="genres-listing-item-button-top">
                                    <Icon name="ph:music-note"/>
                                </span>
                                <span class="genres-listing-item-button-bottom">
                                    <strong>
                                        {{ genre.name }}
                                    </strong>
                                    <small>
                                        {{ genre.numberOfSongs }} songs
                                    </small>
                                </span>
                            </button>
                        </li>
                    </ul>
                    <button 
                        :disabled="!canScrollGenresLeft" 
                        class="arrow left"
                        @click="handleGenresScroll('left')"
                    >
                        <span class="visually-hidden">Scroll left</span>
                        <Icon name="ph:caret-left"/>
                    </button>
                    <button 
                        :disabled="!canScrollGenresRight" 
                        class="arrow right"
                        @click="handleGenresScroll('right')"
                    >
                        <span class="visually-hidden">Scroll right</span>
                        <Icon name="ph:caret-right"/>
                    </button>
                </div>
            </section>
        </div>
    </section>
</template>

<script setup>

const props = defineProps({
    active: {
        type: Boolean,
        default: false
    }
})

const { active } = toRefs(props)

const emits = defineEmits(['close:player'])

const genresElements = ref(null)
const genresContainerElement = ref(null)

onMounted(() => {
    const options = {
        root: genresContainerElement.value,
        rootMargin: '0px',
        threshold: 1.0
    }

    const observer = new IntersectionObserver(test, options)
    observer.observe(genresElements.value[0])
    observer.observe(genresElements.value.at(-1))
})

function test(event) {
    event.forEach(entry => {
        if(entry.target == genresElements.value[0]) {
            canScrollGenresLeft.value = !entry.isIntersecting
        }
        if(entry.target == genresElements.value.at(-1)) {
            canScrollGenresRight.value = !entry.isIntersecting
        }
    })
}

const genres = reactive([
    {
        id: 1,
        name: 'Rock',
        numberOfSongs: 120
    },
    {
        id: 2,
        name: 'Classical',
        numberOfSongs: 20
    },
    {
        id: 3,
        name: 'Pop',
        numberOfSongs: 110
    },
    {
        id: 4,
        name: 'Rap',
        numberOfSongs: 110
    },
    {
        id: 5,
        name: 'Indie',
        numberOfSongs: 30
    },
    {
        id: 6,
        name: 'Electronic ',
        numberOfSongs: 130
    },
    {
        id: 7,
        name: 'Jazz ',
        numberOfSongs: 130
    }
])

const genresCarouselPosition = ref('0')

function handleGenresScroll(direction) {
    
    if(direction == 'left') {
        if(!canScrollGenresLeft.value) return
        genresCarouselPosition.value = (Number(genresCarouselPosition.value.replace('%', '')) + 50) + '%'
        return
    }

    if(!canScrollGenresRight.value) return

    genresCarouselPosition.value = (Number(genresCarouselPosition.value.replace('%', '')) - 50) + '%'
}

const canScrollGenresLeft = ref(false)

const canScrollGenresRight = ref(true)
</script>

<style lang="scss" scoped>

.player {
        position: fixed;
        inset: 0;
        clip-path: circle(0%);
        transition: clip-path 2s ease;
        color: $text_color;
        
        &:after {
            content: '';
            position: fixed;
            inset: 0;
            background-color: $background-color;
        }

        .background {
            z-index: 2;
            position: relative;
        }

        &.active {
            clip-path: circle(100%);
        }
        &-content {
            position: relative;
            z-index: 3;
            .header {
                display: flex;
                align-items: center;
                gap: 40px;
                margin: 20px 32px;

                .search-wrapper {
                    flex-grow: 1;
                }
            }

            .section-title {
                font-size: 28px;
                font-weight: 500;
                margin-bottom: 12px;
            }
            .genres {
                margin: 32px;
                $item_height: 200px;
                &-container {
                    position: relative;
                    height: $item_height;
                    max-width: 100%;
                    overflow: hidden;
                    .arrow {
                        position: absolute;
                        top: -5px;
                        height: calc(100% + 10px);
                        width: 140px;
                        z-index: 1;
                        border-radius: 12px;
                        display: flex;
                        flex-direction: column;
                        justify-content: center;
                        padding: 0;
                        border: none;
                        font-size: 40px;
                        background-color: transparent;
                        color: $text-color;
                        opacity: 0;
                        transition: opacity 0.3s ease;
                        
                        &:hover {
                                opacity: 1;
                        }
                        &.left {
                            left: -5px;
                            padding-left: 20px;
                            background-image: linear-gradient(90deg, $background-color 2%, transparent);
                            &:disabled {
                                left: -1000000000px;
                            }
                        }
                        &.right {
                            right: -5px;
                            padding-right: 20px;
                            align-items: flex-end;
                            background-image: linear-gradient(-90deg, $background-color 2%, transparent);
                            &:disabled {
                                right: -1000000000px;
                            }
                        }
                    }
                }
                &-listing {
                    display: flex;
                    align-items: center;
                    gap: 16px;
                    position: absolute;
                    left: v-bind(genresCarouselPosition);
                    transition: left 0.5s ease;
                    &:hover {
                        & ~ .arrow:not(:disabled) {
                            opacity: 1;
                        }
                    }
                    &-item {
                        &-button {
                            padding: 0;
                            color: $text_color;
                            border: none;
                            width: 320px;
                            height: 200px;
                            border-radius: 12px;
                            border: 1px solid rgba($pure_white, 0.6);
                            display: flex;
                            flex-direction: column;
                            justify-content: space-between;

                            &:focus {
                                outline: transparent;
                            }
                            
                            &.rock {
                                background-image: linear-gradient(to right, #f78ca0 0%, #f9748f 19%, #fd868c 60%, #fe9a8b 100%);
                            }

                            &.classical {
                                background-image: linear-gradient(to top, #88d3ce 0%, #6e45e2 100%);
                            }

                            &.pop {
                                background-image: linear-gradient(to top, #7028e4 0%, #e5b2ca 100%);
                            }

                            &.rap {
                                background-image: linear-gradient(-60deg, #ff5858 0%, #f09819 100%);
                            }

                            &.indie {
                                background-image: linear-gradient(-20deg, #ddd6f3 0%, #faaca8 100%, #faaca8 100%);
                            }

                            &.electronic {
                                background-image: linear-gradient(120deg, #fcc5e4 0%, #fda34b 15%, #ff7882 35%, #c8699e 52%, #7046aa 71%, #0c1db8 87%, #020f75 100%);
                            }

                            &.jazz {
                                background-image: linear-gradient(to right, #92fe9d 0%, #00c9ff 100%);
                            }

                            &-top {
                                padding: 20px;
                                svg {
                                    padding: 4px;
                                    background-color: rgba($pure_white, 0.2);
                                    border-radius: 50%;
                                    font-size: 28px;
                                    border: 1px solid rgba($pure_white, 0.6);
                                }
                            }

                            &-bottom {
                                width: 100%;
                                backdrop-filter: blur(8px);
                                border-radius: 0 0 12px 12px;
                                border-top: 1px solid rgba($pure_white, 0.6);
                                display: flex;
                                flex-direction: column;
                                justify-content: center;
                                padding: 12px;
                                text-align: left;
                            }
                        }
                    }
                }
            }
        }
    }
</style>