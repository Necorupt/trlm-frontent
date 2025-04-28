<template>
  <footer class="footer">
    <div class="footer__links">
      <a href="#" class="footer__link">Подбор запчастей</a>
      <a href="#" class="footer__link">Доставка</a
      ><a href="#" class="footer__link">Как купить</a>
      <router-link :to="{name:'payment'}" class="footer__link">Оплата</router-link>
      <a href="#" class="footer__link">Договор оферты</a>
      <a href="#" class="footer__link">Политика конфиденциальности</a
      ><a href="#" class="footer__link">Реквизиты</a>
      <a href="#" class="footer__link">Контакты</a
      ><a href="#" class="footer__link">Акции</a>
    </div>
    <div class="footer__social">
      <div class="footer__socials">
        <a href="#"><vk /></a>
        <a href="#"><whats-up /></a>
        <a href="#"><instagramm /></a>
      </div>
    </div>
  </footer>
</template>

<script>
import Vk from "@/components/icons/Vk.vue";
import WhatsUp from "@/components/icons/WhatsUp.vue";
import Instagramm from "@/components/icons/Instagramm.vue";

export default {
  components: {
    Vk,
    WhatsUp,
    Instagramm,
  },
};
</script>