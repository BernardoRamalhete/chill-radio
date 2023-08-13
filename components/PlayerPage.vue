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
            <PlayerPageGenresCarousel/>
        </div>
        <aside class="player-sidebar">
            <h2 class="title">
                Now playing
            </h2>
            <ul class="playlist">
                <li 
                    v-for="music in playlist" 
                    :key="music.id"
                    class="music"
                >
                    <img :src="music.picture" alt=""/>
                    <span class="music-text">
                        <strong>{{ music.name }}</strong>
                        <small>{{ music.artist }}</small>
                    </span>
                    <button class="music-actions">
                        <span class="visually-hidden">Actions for {{ music.name }}</span>
                        <Icon name="ph:dots-three-vertical"/>
                    </button>
                </li>
            </ul>
        </aside>
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

const playlist = reactive([
    {
        id: 'music_1',
        name: 'Freak Show',
        artist: 'Jake Daniels, AViVA',
        picture: 'https://picsum.photos/seed/music_1/200'
    },
    {
        id: 'music_2',
        name: 'Bad Side',
        artist: 'Jake Daniels',
        picture: 'https://picsum.photos/seed/music_2/200'
    },
    {
        id: 'music_3',
        name: 'BAD BITCH',
        artist: 'Tessa Violet',
        picture: 'https://picsum.photos/seed/music_3/200'
    },
    {
        id: 'music_4',
        name: 'AMERICAN HORROR SHOW',
        artist: 'SNOW WIFE',
        picture: 'https://picsum.photos/seed/music_4/200'
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
        display: flex;
        
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
            flex-grow: 1;
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
        }

        &-sidebar {
            z-index: 2;
            background-color: lighten($background_color, 2%);
            padding: 20px 80px;
            .title {
                font-weight: 500;
                font-size: 18px;
            }
        }
    }
</style>