<template>
    <div class="carousel-container">
        <div class="carousel">
            <div v-for="(image, index) in images" :key="index" :style="{ backgroundImage: `url(${image})` }"
                :class="{ 'carousel-item': true, active: index === currentIndex }"></div>
        </div>

        <div class="carousel-caption-overlay">
            <div class="content animate__animated animate__slideInDown">
                <h1 class="mb-3">Welcome to <strong>Scrutz</strong></h1>
                <h6>Do you have a campaign and you do not know how to go about it ?</h6>
                    <h6>Trust us with your campaign and we will give you the very best experience.</h6>
            </div>
            <router-link to="/login" class="btn custom-btn btn-lg mt-4 skill">Get Started</router-link>
        </div>
    </div>

</template>

<script>
export default {


    data() {
        return {

            images: [
                '/images/newImg.jpg',
            ],
            currentIndex: 0,
            intervalTime: 2000,
        };
    },
    mounted() {
        this.startCarousel();
    },
    methods: {
        
        startCarousel() {
            setInterval(() => {

                this.currentIndex = (this.currentIndex + 1) % this.images.length;
            }, this.intervalTime);
        },
    },
};
</script>

<style>
.carousel-container {
    position: relative;
    width: 100%;
    height: 100vh;
    overflow: hidden;
}

.carousel {
    position: absolute;
    width: 100%;
    height: 100%;
}

.carousel-item {
    min-width: 100%;
    height: 100%;
    background-size: cover;
    background-position: center;
    position: absolute;
    top: 0;
    left: 0;
    opacity: 0;
    transition: opacity 1s ease-in-out;
}

.carousel-item.active {
    opacity: 1;
}

.carousel-caption-overlay {
    position: absolute;
    bottom: 0;
    top: 0;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.4);
    color: white;
    text-align: center;
    /* border: 1px solid aqua; */

}

.carousel-caption-overlay>div {
    margin-top: 220px;
}

.btn.custom-btn:hover {
    border: 3px solid;
    border-color: #247B7B;
    color: white;
}

.btn.custom-btn {
    background: #247B7B;
    color: white;
}
.skill {
    background: #6a11cb;
    padding: 10px 20px;
    border-radius:20px;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.5);
    animation: pop 2s ease-in-out infinite alternate;
}

@keyframes pop {
    from {
        transform: scale(1);
    } 
    to {
        transform: scale(1.1);
    }
}
h6 {
    line-height: 2;
    width: 50%;
    margin: 0 auto;
}


</style>
