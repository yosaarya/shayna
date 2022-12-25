<template>
  <div class="home">
   <HeaderShayna />
   <HeroSection />
   <WomanBanner />
   <InstaShayna />
   <PartnerLogo />
   <FooterShayna />

  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import HeaderShayna from '@/components/HeaderShayna.vue'
import HeroSection from '@/components/HeroSection.vue'
import WomanBanner from '@/components/WomanBanner.vue'
import InstaShayna from '@/components/InstaShayna.vue'
import PartnerLogo from '@/components/PartnerLogo.vue'
import FooterShayna from '@/components/FooterShayna.vue'

export default {
  name: 'HomeView',
  components: {
    HeaderShayna,
    HeroSection,
    WomanBanner,
    InstaShayna,
    PartnerLogo,
    FooterShayna
  }
}
</script>
