<template>
  <div class="home-page">
    <slider class="home-page__slider" :slides="slides" />
    <div class="home-page__content">
      <div class="home-page__advantages">
        <div
          class="home-page__advantage"
          v-for="(adavantage, index) in advantages"
        >
          <h3 class="home-page__advantage-number">
            {{ (index + 1 != 0 && index + 1 < 9 ? "0" : "") + (index + 1) }}
          </h3>
          <div class="home-page__advantage-content">
            <h2>{{ adavantage.title }}</h2>
            <p>{{ adavantage.description }}</p>
            <a
              :href="adavantage.link"
              class="button"
              :class="
                adavantage.link_type === 'tel'
                  ? 'button-green-border'
                  : 'button-main-border'
              "
              >{{ adavantage.link_text }}</a
            >
          </div>
        </div>
      </div>
      <div class="home-page__offers">
        <div class="home-page__offer home-page__offers-sm">
          <div class="home-page__offer-content">
            <h1 class="home-page__offer-title">Щетки AWM</h1>
            <a href="#" class="home-page__offer-link">Подробнее</a>
          </div>
          <img
            class="home-page__offer-image"
            src="@/assets/images/Offer-1.png"
            alt=""
          />
        </div>
        <div class="home-page__offer home-page__offers-large">
          <div class="home-page__offer-content">
            <h3 class="home-page__offer-text">Весь январь</h3>
            <h1 class="home-page__offer-title">скидка 20% на весь DOT4</h1>
            <a href="#" class="home-page__offer-link">Подробнее</a>
          </div>
          <img
            class="home-page__offer-image"
            src="@/assets/images/Offer-2.png"
            alt=""
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Slider from "@/components/Home/Slider.vue";

export default {
  data() {
    return {
      slides: [
        {
          background: "/src/assets/images/HomeSlideBgr-1.png",
          foreground: "/src/assets/images/HomeSlideFg-1.png",
        },
        {
          background: "/src/assets/images/HomeSlideBgr-2.png",
          foreground: "/src/assets/images/HomeSlideFg-2.png",
        },
      ],
      advantages: [
        {
          title: "Бесплатный звонок",
          description: "На любые номера РФ",
          link: "tel:0000000000",
          link_type: "tel",
          link_text: "+7 (928) 107-80-80",
        },
        {
          title: "Бесплатный подбор",
          description:
            "Мы найдем самую низкую цену на оригинальную запчасть, достойную альтернативу или самый дешевый аналог.",
          link: "#",
          link_text: "Заявка на подбор",
        },
        {
          title: "Бесплатная доставка",
          description:
            "Согласуем и привезём запчасти в офис или домой в удобное для Вас время.",
          link: "#",
          link_text: "Пункты выдачи",
        },
      ],
    };
  },
  components: {
    Slider,
  },
};
</script>

<style>
.home-page {
  padding: 50px 40px;
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.home-page__slider {
  position: absolute;
  width: calc(100% - 40px * 2);
}

.home-page__content{
  margin-top: 300px;
  z-index: 20;
  padding: 0px 190px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.home-page__advantages {
  z-index: 30;
  display: flex;
  gap: 30px;
}

.home-page__advantage {
  box-shadow: 0 0 1px 0 rgba(0, 0, 0, 0.04), 0 2px 6px 0 rgba(0, 0, 0, 0.04),
    0 10px 20px 0 rgba(0, 0, 0, 0.04);
  background: #fff;
  padding: 32px 16px;
  display: flex;
  gap: 8px;
  width: 100%;
}

.home-page__advantage-number {
  font-family: var(--font-family);
  font-weight: 900;
  font-size: 36px;
  line-height: 100%;
  text-align: center;
  color: rgba(34, 34, 34, 0.2);
}

.home-page__advantage-content {
  display: flex;
  flex-direction: column;
  gap: 16px;
  justify-content: space-between;
}

.home-page__offers {
  position: relative;
  display: flex;
  flex-direction: row;
  gap: 30px;
  height: 360px;
}

.home-page__offer {
  position: relative;
  display: flex;
  min-width: 460px;
}

.home-page__offer-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  z-index: -1;
  inset: 0;
}

.home-page__offer-content {
  position: absolute;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 40px;
  height: calc(100% - 40px * 2);
}

.home-page__offer-title {
  color: white;
  text-align: left;
  width: 200px;
  margin: 0;
}

.home-page__offer-text {
  color: white;
  margin: 0;
}

.home-page__offer-link {
  font-family: var(--font-family);
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
  text-transform: uppercase;
  color: #fff;
  text-decoration: underline;
}
</style>
