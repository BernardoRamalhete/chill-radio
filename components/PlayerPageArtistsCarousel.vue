<template>
    <div class="artists">
        <h2 class=section-title>
            World's biggest names putting on a show just for you
        </h2>
        <div class="artists-content"></div>
        <ul class="artists-content-listing">
            <li 
                v-for="(artist, index) in artists" 
                :key="artist.name"
                class="artists-content-listing-item"
            >
                <span class="text">
                    <h3>{{ artist.name }}</h3>
                    <small>{{ artist.genre }}</small>
                </span>
                <figure class="image-wrapper" :class="getClassName(index)">
                    <img :src="artist.picture" alt=""/>
                </figure>
                <AppButton class="green button">
                    Next
                    <Icon name="ph:arrow-right"/>
                </AppButton>
            </li>
        </ul>
    </div>
</template>

<script setup>
const artists = reactive([
    {
        name: 'Bruno Mars',
        genre: 'Pop',
        picture: 'https://www.pngall.com/wp-content/uploads/5/Singer-Bruno-Mars-PNG-Image-File.png',
        color: 'whitesmoke'
    },
    {
        name: 'Eminem',
        genre: 'Rap',
        picture: 'https://www.pngall.com/wp-content/uploads/2016/03/Eminem-Rapper-PNG.png'
    },
    {
        name: 'Imagine Dragons',
        genre: 'Indie',
        picture: 'https://www.pngall.com/wp-content/uploads/5/Imagine-Dragons-PNG-Download-Image.png'
    },
    {
        name: 'Ozzy Osbourne',
        genre: 'Rock',
        picture: 'https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/1bee66ba-7191-4b0c-9f0b-d43ea813cb5a/dehu0na-ea2d8da9-7456-4ab1-b1d5-411c9a79e12f.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzFiZWU2NmJhLTcxOTEtNGIwYy05ZjBiLWQ0M2VhODEzY2I1YVwvZGVodTBuYS1lYTJkOGRhOS03NDU2LTRhYjEtYjFkNS00MTFjOWE3OWUxMmYucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.NTMzs_Gc3oLU5YMsOevmfAI_nQvynW1dDHkDbJLbCsU'
    },
    {
        name: 'Steve Aoki',
        genre: 'Eletronic',
        picture: 'https://static.tumblr.com/f0ltvif/RlWm94bfk/aoki_jumping_cutout.png'
    },
    {
        name: 'Bruno Mars',
        genre: 'Pop',
        picture: 'https://www.pngall.com/wp-content/uploads/5/Singer-Bruno-Mars-PNG-Image-File.png',
        color: 'whitesmoke'
    },
    {
        name: 'Eminem',
        genre: 'Rap',
        picture: 'https://www.pngall.com/wp-content/uploads/2016/03/Eminem-Rapper-PNG.png'
    },
    {
        name: 'Imagine Dragons',
        genre: 'Indie',
        picture: 'https://www.pngall.com/wp-content/uploads/5/Imagine-Dragons-PNG-Download-Image.png'
    },
    {
        name: 'Ozzy Osbourne',
        genre: 'Rock',
        picture: 'https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/1bee66ba-7191-4b0c-9f0b-d43ea813cb5a/dehu0na-ea2d8da9-7456-4ab1-b1d5-411c9a79e12f.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzFiZWU2NmJhLTcxOTEtNGIwYy05ZjBiLWQ0M2VhODEzY2I1YVwvZGVodTBuYS1lYTJkOGRhOS03NDU2LTRhYjEtYjFkNS00MTFjOWE3OWUxMmYucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.NTMzs_Gc3oLU5YMsOevmfAI_nQvynW1dDHkDbJLbCsU'
    },
    {
        name: 'Steve Aoki',
        genre: 'Eletronic',
        picture: 'https://static.tumblr.com/f0ltvif/RlWm94bfk/aoki_jumping_cutout.png'
    }
])


function getClassName(index) {
    if(index < 5) return `color-${Math.abs(index+1)}`

    return getClassName(index - 5)
}
</script>

<style lang="scss" scoped>
.artists {
    margin: 32px;

    &-content {
        &-listing {
            display: flex;
            align-items: center;
            gap: 20px;
            &-item {
                display: flex;
                align-items: center;
                gap: 12px;

                .image-wrapper {
                    width: 200px;
                    height: 400px;
                    border-radius: 200px;
                    overflow: hidden;
                    position: relative;
                    flex-shrink: 0;
                    &.color-1 {
                        background-color: $blob_yellow;
                    }
                    &.color-2 {
                        background-color: $light_blue;
                        
                    }
                    &.color-3 {
                        background-color: $pink;
                        
                    }
                    &.color-4 {
                        background-color: $primary_orange;
                        
                    }
                    &.color-5 {
                        
                        background-color: $primary_purple;
                    }

                    img {
                        width: 100%;
                        height: 90%;
                        position: absolute; 
                        bottom: - 50px;
                        object-fit: cover;
                        object-position: bottom;
                    }
                }
            }
        }
    }
}
</style>