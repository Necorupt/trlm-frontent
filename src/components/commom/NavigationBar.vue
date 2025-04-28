<template>
  <nav class="navigation">
    <router-link :to="{ name: 'home' }">
      <img class="navigation__logo" src="@/assets/icons/Logo.png" alt="" />
    </router-link>
    <div class="navigation__selectors">
      <div class="selector">
        <h4>Малиновского</h4>
        <arrow />
      </div>
      <a href="#" class="button button-main">Каталог</a>
    </div>

    <div class="navigation-search">
      <div class="navigation-search-top">
        <div class="navigation-contacts">
          <h4>8-800-550-19-80</h4>
          <div class="navigation__links">
            <a href="#" class="link">Подбор запчастей</a>
            <a href="#" class="link">Доставка</a>
            <a href="#" class="link">Как купить</a>
            <router-link :to="{ name: 'payment' }" class="link"
              >Оплата</router-link
            >
            <a href="#" class="link">Акции</a>
            <a href="#" class="link">Контакты</a>
          </div>
        </div>
        <div class="navigaion__profile">
          <a class="navigation__profile-item" href="#">
            <profile />
            <h4>Войти</h4>
          </a>
          <a class="navigation__profile-item" href="#">
            <cart />
            <h4>Корзина</h4>
          </a>
        </div>
      </div>
      <input type="text" class="navigation__search-input" />
    </div>
  </nav>
</template>

<script>
import Arrow from "@/components/icons/Arrow.vue";
import Profile from "@/components/icons/Profile.vue";
import Cart from "@/components/icons/Cart.vue";

export default {
  components: {
    Arrow,
    Profile,
    Cart,
  },
};
</script>
