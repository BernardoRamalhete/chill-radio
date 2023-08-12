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
                <ul class="genres-listing">
                    <li
                        v-for="genre in genres" :key="genre.id"
                        class="genres-listing-item"
                    >
                        <button 
                            class="genres-listing-item-button" 
                            :class="genre.name.toLowerCase()"
                        >
                            <span class="genres-listing-item-button-top">
                                <Icon name="ph:music-note"/>
                            </span>
                            <span class="genres-listing-item-button-bottom">
                                {{ genre.name }}
                                {{ genre.numberOfSongs }} songs
                            </span>
                        </button>
                    </li>
                </ul>
            </section>
        </div>
    </section>
</template>

<script setup>
import { toRefs } from '#imports'

const props = defineProps({
    active: {
        type: Boolean,
        default: false
    }
})

const { active } = toRefs(props)

const emits = defineEmits(['close:player'])

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
            }
            .genres {
                margin: 0 32px;
                &-listing {
                    display: flex;
                    align-items: center;
                    gap: 16px;
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
                                height: 60px;
                                backdrop-filter: blur(8px);
                                border-radius: 0 0 12px 12px;
                                border-top: 1px solid rgba($pure_white, 0.6);
                                display: flex;
                                flex-direction: column;
                                justify-content: center;
                                padding-left: 12px;
                                text-align: left;
                            }
                        }
                    }
                }
            }
        }
    }
</style>