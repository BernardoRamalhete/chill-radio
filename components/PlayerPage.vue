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
        <PlayerPageSidebar/>
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
            background-color: $background_color;
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
            z-index: 2;
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
    }
</style>