<template>
  <navigation-bar />
  <router-view />
  <Footer />
</template>

<script>
import NavigationBar from "@/components/commom/NavigationBar.vue";
import Footer from '@/components/commom/Footer.vue'

export default {
  components: {
    NavigationBar,
    Footer,
  },
};
</script>
