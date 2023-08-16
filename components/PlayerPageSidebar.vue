<template>
    <aside class="player-sidebar">
        <h2 class="title">
            Next on your playlist
        </h2>
        <ul class="playlist">
            <li 
                v-for="music in playlist" 
                :key="music.id"
                class="music"
            >
                <div>
                    <button v-if="music.id == 'music_4'" class="music-toggle">
                        <Icon v-if="true" name="ph:pause-fill"/>
                        <Icon v-else name="ph:play-fill"/>
                    </button>
                    <img :src="music.picture" alt="" class="music-cover"/>
                    <span class="music-text">
                        <strong class="music-text-title">{{ music.name }}</strong>
                        <small class="music-text-artist">{{ music.artist }}</small>
                    </span>
                    <button 
                        class="music-actions" 
                        :class="{ 'on-top': activeMusicActions == music.id }"
                        @click="openMusicActions(music.id)"
                    >
                        <span class="visually-hidden">Actions for {{ music.name }}</span>
                        <Icon name="ph:dots-three-vertical"/>
                    </button>
                </div>
                <!-- v-if="activeMusicActions == music.id"  -->
                <span
                    :class="{ active: activeMusicActions == music.id }"
                >
                    <ul class="music-actions-options">
                        <li class="gradient"/>
                        <li>
                            <button class="action">
                                Remove from queue
                            </button>
                        </li>
                        <li>
                            <button class="action">
                                View artist
                            </button>
                        </li>
                    </ul>
                </span>
            </li>
        </ul>
        <div class="controls">
            <img :src="playlist[0].picture" alt="" class="controls-cover"/>
            <span class="controls-content">
                <strong class="controls-content-title">{{ playlist[0].name }}</strong>
                <small class="controls-content-artist">{{ playlist[0].artist }}</small>
                <span class="controls-content-actions">
                    <span class="controls-content-actions-buttons">
                        <button>
                            <span class="visually-hidden">Play previous sound</span>
                            <Icon name="ph:skip-back-fill"/>
                        </button>
                        <button v-if="true">
                            <span class="visually-hidden">Play</span>
                            <Icon name="ph:play-fill"/>
                        </button>
                        <button v-else>
                            <span class="visually-hidden">Pause</span>
                            <Icon name="ph:pause-fill"/>
                        </button>
                        <button>
                            <span class="visually-hidden">Play next sound</span>
                            <Icon name="ph:skip-forward-fill"/>
                        </button>
                    </span>
                    <label for="track" class="visually-hidden">
                        Navigate through current sound
                    </label>
                    <AppMusicTrack inputId="track"/>
                </span>
            </span>
        </div>
    </aside>
</template>

<script setup>

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
    },
    {
        id: 'music_5',
        name: 'Freak Show',
        artist: 'Jake Daniels, AViVA',
        picture: 'https://picsum.photos/seed/music_1/200'
    },
    {
        id: 'music_6',
        name: 'Bad Side',
        artist: 'Jake Daniels',
        picture: 'https://picsum.photos/seed/music_2/200'
    },
    {
        id: 'music_7',
        name: 'BAD BITCH',
        artist: 'Tessa Violet',
        picture: 'https://picsum.photos/seed/music_3/200'
    },
    {
        id: 'music_8',
        name: 'AMERICAN HORROR SHOW',
        artist: 'SNOW WIFE',
        picture: 'https://picsum.photos/seed/music_4/200'
    },
    {
        id: 'music_9',
        name: 'Freak Show',
        artist: 'Jake Daniels, AViVA',
        picture: 'https://picsum.photos/seed/music_1/200'
    },
    {
        id: 'music_10',
        name: 'Bad Side',
        artist: 'Jake Daniels',
        picture: 'https://picsum.photos/seed/music_2/200'
    },
    {
        id: 'music_11',
        name: 'BAD BITCH',
        artist: 'Tessa Violet',
        picture: 'https://picsum.photos/seed/music_3/200'
    },
    {
        id: 'music_12',
        name: 'AMERICAN HORROR SHOW',
        artist: 'SNOW WIFE',
        picture: 'https://picsum.photos/seed/music_4/200'
    },
    {
        id: 'music_13',
        name: 'Freak Show',
        artist: 'Jake Daniels, AViVA',
        picture: 'https://picsum.photos/seed/music_1/200'
    },
    {
        id: 'music_14',
        name: 'Bad Side',
        artist: 'Jake Daniels',
        picture: 'https://picsum.photos/seed/music_2/200'
    },
    {
        id: 'music_15',
        name: 'BAD BITCH',
        artist: 'Tessa Violet',
        picture: 'https://picsum.photos/seed/music_3/200'
    },
    {
        id: 'music_16',
        name: 'AMERICAN HORROR SHOW',
        artist: 'SNOW WIFE',
        picture: 'https://picsum.photos/seed/music_4/200'
    },
])


const activeMusicActions = ref(null)

function openMusicActions(musicId) {
    if(activeMusicActions.value == musicId) {
        closeMusicActions()
        return
    }
    activeMusicActions.value = musicId
}

function closeMusicActions() {
    activeMusicActions.value = null
}
</script>

<style lang="scss" scoped>
.player-sidebar {
    z-index: 2;
    background-color: lighten($background_color, 2%);
    padding: 20px 40px;
    display: flex;
    flex-direction: column;
    position: relative;
    .title {
        font-weight: 400;
        font-size: 16px;
    }
    .playlist {
        display: flex;
        flex-direction: column;
        padding-right: 20px;
        gap: 16px;
        flex-grow: 1;
        max-height: 100%;
        overflow-y: auto;
        overflow-x: visible;
        margin-block: 12px 28px;
        .music {
            position: relative;
            & > div {
                display: flex;
                align-items: center;
            }
            & > span {
                display: grid;
                grid-template-rows: 0fr;
                transition: grid-template-rows 0.3s ease;
                overflow: hidden;
                position: absolute;
                top: 50%;
                width: 100%;
                border-radius: 0 0 12px 12px;
                &.active {
                    grid-template-rows: 1fr;
                    border: 1px solid rgba($text_color, 0.2);
                    border-top: none;
                }
            }
            &-toggle {
                background-color: rgba($background_color, 0.6);
                border: none;
                position: absolute;
                width: 48px;
                aspect-ratio: 1;
                color: $text_color;
                font-size: 24px;
                &:focus {
                    outline: transparent;
                }
            }
            &-cover {
                max-width: 48px;
                border-radius: 4px;
            }
            &-text {
                display: flex;
                flex-direction: column;
                margin-inline: 8px;
                flex-grow: 1;
                &-title {
                    font-weight: 500;
                    font-size: 14px;
                }
                &-artist {
                    font-size: 12px;
                    white-space: nowrap;
                    overflow: hidden;
                    max-width: 16ch;
                    text-overflow: ellipsis;
                }
            }
            &-actions { 
                background-color: transparent;
                color: $text_color;
                font-size: 24px;
                padding: 2px;
                border: none;
                cursor: pointer;
                &.on-top {
                    z-index: 3;
                }
                &:focus {
                    outline: transparent;
                }
                
                &-options {
                    overflow: hidden;
                    min-width: fit-content;
                    z-index: 2;
                    border-top: none;
                    li {
                        .action {
                            border: none;
                            width: 100%;
                            background-color: $background_color;
                            padding: 12px;
                            text-align: left;
                            white-space: nowrap;
                            border-bottom: 1px solid rgba($text_color, 0.2);
                            font-size: 14px;
                            color: $text_color;
                            transition: background-color 0.2s ease;
                            cursor: pointer;
                            &:hover {
                                background-color: lighten($background_color, 2%);
                            }
                            &:focus {
                                outline: transparent;
                            }
                        }

                        &.gradient {
                            background-color: transparent;
                            height: 30px;
                            width: 100%;
                            background: linear-gradient(transparent, $background_color);
                        }

                        &:last-of-type {
                            .action {
                                border: none;
                            }
                        }
                    }
                }
            }
        }
    }

    .controls {
        position: relative;
        &-cover {
            width: 100%;
            border-radius: 12px;
        }

        &-content {
            min-width: 94%;
            position: absolute;
            bottom: 8px;
            left: 50%;
            padding: 20px 16px;
            transform: translateX(-50%);
            background-color: rgba($background_color, 0.8);
            backdrop-filter: blur(8px);
            border-radius: 8px;
            display: flex;
            flex-direction: column;
            align-items: center;

            &-title {
                font-weight: 500;
            }

            &-artist {
                font-size: 12px;
                color: rgba($text_color, 0.8);
                margin-block: 4px 8px;
            }

            &-actions {
                display: flex;
                flex-direction: column;
                align-items: center;
                gap: 4px;
                &-buttons {
                    display: flex;
                    gap: 12px;
                    button {
                        padding: 4px;
                        border: none;
                        background-color: transparent;
                        color: $text_color;
                        font-size: 24px;
                        &:focus {
                            outline: transparent;
                        }
                    }
                }
            }
        }
    }
        
}
</style>