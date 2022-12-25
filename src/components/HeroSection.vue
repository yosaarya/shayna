<template>
    <div>
         <!-- Hero Section Begin -->
   <section class="hero-section">
        <carousel :items-to-show="1">
            <slide v-for="slide in 5" :key="slide">
            <!-- First Content Start -->
          <div class="single-hero-items set-bg" style="background-image:url('/img/hero-1.jpg')">
                <div class="container">
                    <div class="row" banner-info>
                        <div class="col-lg-5">
                            <span>Bag,kids</span>
                            <h1>Black friday</h1>
                            <p>
                                Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore
                            </p>
                            <a href="#" class="primary-btn">Shop Now</a>
                        </div>
                    </div>
                </div>
            </div>
            <!-- First Content End -->
            </slide>
            <template #addons>
                 <navigation />
                 <pagination />
             </template>
          </carousel>
    </section>
    <!-- Hero Section End -->
    </div>
</template>

<!-- <template>
    <carousel :items-to-show="1.5">
      <slide v-for="slide in 10" :key="slide">
        {{ slide }}
      </slide>
  
      <template #addons>
        <navigation />
        <pagination />
      </template>
    </carousel>
  </template> -->

<script>

import "vue3-carousel/dist/carousel.css";
import {Carousel,Slide, Pagination, Navigation} from "vue3-carousel";
export default {
    name:"HeroSection",
    components:{
        Carousel,
        Slide,
        Pagination,
        Navigation
    }
}
</script>

<style>
.set-bg{
    width: 100%;
    height: 500px;
}
.banner-info{
    margin-top: 130px;
}
</style>