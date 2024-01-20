<template>
    <div class="gallery-page container">
        <div class="principal">
            <headerComponent />
            <div class="principal-text p-4">
                <h1>GALERIA</h1>
                <h3>Veja as fotos da nossa igreja</h3>
            </div>
        </div>
        <optionsBackground style="width: 100%;">
            <div class="gallery-container">
                <div ref="swiper" class="swiper">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide" v-for="(image, index) in images" :key="index">
                            <img :src="image" class="img-fluid">
                        </div>
                    </div>
                    <div class="swiper-pagination"></div>

                    <div class="swiper-button-prev"></div>
                    <div class="swiper-button-next"></div>

                    <div class="swiper-scrollbar"></div>
                </div>
            </div>   
        </optionsBackground>
        <footerComponent />
    </div>
</template>
<script>
import headerComponent from "../components/headerComponent.vue";
import optionsBackground from "../components/optionsBackground.vue";
import footerComponent from "../components/footerComponent.vue";

import Swiper, { Navigation, Pagination, EffectCards } from 'swiper';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/autoplay';

export default {
    name: "galleryPage",
    data() {
        return {
            images: []
        }
    },
    components: {
        headerComponent,
        optionsBackground,
        footerComponent
    },
    mounted: function () {
        this.swiper = new Swiper(this.$refs.swiper, {
            modules: [Navigation, Pagination, EffectCards],
            loop: true,
            pagination: {
                el: '.swiper-pagination',
                clickable: true
            },
            scrollbar: {
                el: '.swiper-scrollbar',
            },
            navigation: {
                nextEl: '.swiper-button-next',
                prevEl: '.swiper-button-prev',
            },
            slidesPerView: 1,
            centeredSlides: true,
            centeredSlidesBounds: true,
            slideToClickedSlide: true,
            effect: 'cards',
            cardsEffect: {
                perSlideOffset: 16
            },
        })

        const imageContext = require.context('@/assets/img/galeria', false, /\.(png|jpe?g|svg)$/);

        // Passe pelas chaves do contexto e adicione os caminhos das imagens ao array
        imageContext.keys().forEach((key) => {
            this.images.push(imageContext(key));
        });
    }
}
</script>
<style scoped>
.gallery-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 1rem;
    height: 70vh;
    width: 100%;
}

.swiper {
    width: 100%;
    max-width: calc(1000px - 1%);
    height: 100%;
    margin: auto;
}

.swiper-slide {
    border-radius: 1rem;
    width: 100%;
    height: 100%;
    display: flex;
}

    .swiper-slide img {
        width: 100%;
        object-fit: cover;
    }

    .swiper-slide p {
        position: absolute;
        bottom: 1rem;
        left: 0;
        right: 0;
        margin: auto;
        text-align: center;
        color: white;
        font-size: calc(0.4rem + 1vw);
        font-weight: 600;
        background: rgba(0, 0, 0, 0.7);
        padding: calc(0.7rem + 1vw) 0;
    }
</style>