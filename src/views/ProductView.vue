<template>
    <div class="product">
     <HeaderShayna />
        <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/home"><i class="fa fa-home"></i> Home</router-link>
                        <span>Detail</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="row">
                        <div class="col-lg-6">
                            <div class="product-pic-zoom">
                                <img class="product-big-img" :src="gambar_default" alt="" />
                            </div>
                            <div class="product-thumbs">
                                <carousel class="product-thumbs-track ps-slider">
                                    <slide v-for="slide in 1" :key="slide">
                                        <div v-for="ss in productDetails.galleries" :key="ss.id" class="pt" @click="changeImage(ss.photo[0])" :class="ss.photo[0] == gambar_default ? 'active' : '' ">
                                        <img :src="ss.photo" alt="" />
                                        </div>
                                </slide>
                                    <!-- <template #addons> -->
                                        <!-- <navigation /> -->
                                        <!-- <pagination /> -->
                                    <!-- </template> -->
                                </carousel>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="product-details text-left">
                                <div class="pd-title">
                                    <span>{{ productDetails.type }}</span>
                                    <h3>{{ productDetails.name }}</h3>
                                </div>
                                <div class="pd-desc">
                                    <p>
                                        {{ productDetails.description }}
                                    </p>
                                    <h4>${{ productDetails.price }}</h4>
                                </div>
                                <div class="quantity">
                                    <router-link to="/cart" class="primary-btn pd-cart">Add To Cart</router-link>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Product Shop Section End -->
    <RelatedProduct /> 
    <FooterShayna />
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  // import HelloWorld from '@/components/HelloWorld.vue'
  import HeaderShayna from '@/components/HeaderShayna.vue'
  import FooterShayna from '@/components/FooterShayna.vue'
  import RelatedProduct from '@/components/RelatedProduct.vue'
  import "vue3-carousel/dist/carousel.css";
  import {Carousel,Slide, } from "vue3-carousel";
  import axios from "axios";
  
  export default {
    name: 'ProductView',
    components: {
      HeaderShayna,
      FooterShayna,
      Carousel,
      Slide,
      RelatedProduct
    //   Pagination,
    //   Navigation
    },
  data() {
    return{
        gambar_default:"",
        thumbs: [
            "img/mickey1.jpg",
            "img/mickey2.jpg",
            "img/mickey3.jpg",
            "img/mickey4.jpg"
             ],
            productDetails: []
         }
    },
    methods: {
        changeImage(urlImage){
            this.gambar_default = urlImage;
        },
        setDataPicture(data){
            // replace object productDetails dengan data dari API
            this.productDetails = data;
            //replace value gambar default dengan data dari API (galleries)
            this.gambar_default = data.galleries[0].photo;
        },
    },
    mounted(){
        axios
        .get("http://shayna-backend.belajarkoding.com/api/products", {
            params: {
                id: this.$route.params.id
            }
        })
        .then(res => (this.setDataPicture(res.data.data)))
        // eslint-disable-next-line no-console
        .catch(err => console.log(err));
    }
  };
  </script>

<style scoped>
    .product-thumbs .pt{
        margin-right: 10px;
    }
</style>

  