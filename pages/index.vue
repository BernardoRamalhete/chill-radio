<template>
    <div class="wrapper">
        <BlobBackground/>
        <main class="content">
            <section class="hero">
                <h1 class="title">
                    Groovy Beats for Relaxing, Working,<br/> and Jamming While Studying
                </h1>
                <p class="subheading">
                    Elevate your Listening experience: join us on the radio for an eclectic mix of groovy beats, perfectly suited to enhance relaxation, boost productivity, and infuse your study sessions with a fun and lively rhythm!
                </p>
                <AppButton class="primary" text="Start listening"/>
            </section>
        </main>
    </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>
.wrapper {
    height: 100%;
    background-color: $background_color;

    .content {
        position: relative;
        z-index: 2;
        max-width: 1300px;
        margin-inline: auto;

        .hero {
            height: 100vh;
            height: 100dvh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            color: $text_color;
            
            .title {
                text-align: center;
                font-size: 60px;
                position: relative;
                background-image: $title_gradient;
                color: transparent;
                background-clip: text;
            }

            .subheading {
                max-width: 700px;
                text-align: center;
                margin-block: 20px 32px;
                font-size: 18px;
            }
        }
    }

}
</style>