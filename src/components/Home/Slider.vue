<template>
  <div class="slider__wrapper">
    <div class="slider__controlls">
      <button @click="prevSlide">
        <arrow-bg-disabled v-if="canGoBack" class="slider__controlls-left" />
        <arrow-bg v-else class="slider__controlls-left" />
      </button>
      <button @click="nextSlide">
        <arrow-bg-disabled
          v-if="canGoForward"
          class="slider__controlls-right"
        />
        <arrow-bg v-else class="slider__controlls-right" />
      </button>
    </div>

    <div class="slider" :style="computeOffset" ref="slider" v-if="needUpdate">
      <div class="slider__item" v-for="(slide, index) in slides">
        <div class="slider__slide">
          <div class="slider__slide-image">
            <img class="slider__fg-image" :src="slide.foreground" alt="" />
            <img class="slider__bg-image" :src="slide.background" alt="" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ArrowBg from "@/components/icons/ArrowBg.vue";
import ArrowBgDisabled from "@/components/icons/ArrowBgDisabled.vue";

export default {
  props: {
    slides: {
      type: Object,
    },
  },
  components: {
    ArrowBg,
    ArrowBgDisabled,
  },
  data() {
    return {
      needUpdate: true,
      currentSlide: 0,
      slider: null,
    };
  },
  mounted() {
    this.slider = this.$refs.slider;

    const self = this;
    window.addEventListener("resize", () => {
      self.forceUpdate();
    });
  },
  computed: {
    computeOffset() {
      if (this.slider === null) {
        return {
          transform: "translateX(" + 0 + "%)",
        };
      }

      let width = this.slider.getBoundingClientRect().width;
      let offset = (width / this.slides.length) * this.currentSlide;

      return {
        transform: "translateX(" + -offset + "px)",
      };
    },
    canGoBack() {
      return !this.currentSlide > 0;
    },
    canGoForward() {
      return !this.currentSlide < this.slides.length - 1;
    },
  },
  methods: {
    async forceUpdate(){
      // this.needUpdate = false;
      // this.$nextTick(()=>{
      //   this.needUpdate = true;
      //   this.slider = this.$refs.slider;
      // })
    },
    nextSlide() {
      if (this.currentSlide < this.slides.length - 1) {
        this.currentSlide++;
      }
    },
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--;
      }
    },
  },
};
</script>

<style>
.slider__wrapper {
  overflow: hidden;
  position: relative;
}

.slider {
  display: flex;
  flex-direction: row;
  width: auto;
  width: 200vw;
  gap: 80px;
  transition: all 1s ease-in-out;
}

.slider__item {
  width: calc(100vw - 50px * 2);
}

.slider__slide-image {
  display: flex;
  position: relative;
  justify-content: center;
}

.slider__bg-image {
  position: absolute;
  z-index: -1;
  width: 100%;
}

.slider__fg-image {
  width: 297px;
  height: 464px;
  object-fit: contain;
}

.slider__controlls {
  position: absolute;
  z-index: 20;
  right: 180px;
}

.slider__controlls-left {
  transform: rotate(180deg);
}
</style>
