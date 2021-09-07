<template>
  <div class="header">
    <!-- Шапка -->
    <div class="logotip">
      <!-- Оболочка логотипа -->
      <div class="eagle">
        <!-- Орел -->
        <img src="../assets/Logo_eagle.png" />
      </div>
      <div class="ched">
        <!-- ЦХЭД -->
        ЦХЭД
      </div>
    </div>
    <div class="user-menu">
      <!-- Меню пользователя -->
      <div class="notification">
        <!-- Значок уведомлений -->
        <v-btn icon><img src="../assets/Menu_1.png" /></v-btn>
      </div>
      <div class="user">
        <!-- Значок личный кабинет -->
        <v-btn icon><img src="../assets/Menu_2.png" /></v-btn>
      </div>
      <div class="log-out">
        <!-- Значок выйти -->
        <v-btn icon><img src="../assets/Menu_3.png" /></v-btn>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({});
</script>

<style scoped>
.header {
  display: flex;
  flex-direction: row;
  max-height: 64px;
  min-height: 64px;
  background-color: #0c3276;
  align-items: center;
  justify-content: space-between;
  flex: 1;
  width: 100%;
  position: sticky;
  top: 0;
  z-index: 100;
}
.logotip {
  display: flex;
  flex-direction: row;
  flex: 1;
  justify-content: flex-start;
  align-items: center;
  padding-left: 16px;
}
/* .eagle {
  height: 32px;
  width: 32px;
  padding: 16px;
} */
.ched {
  font-family: Golos;
  font-weight: 700;
  font-size: 24px;
  color: #ffffff;
  letter-spacing: 0.1em;
  font-weight: bold;
  line-height: 28px;
  padding-left: 16px;
}
.user-menu {
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  flex: 1;
  justify-content: flex-end;
  align-items: center;
  opacity: 0.5;
}
v-btn {
  background-color: red;
}
.notification {
  padding-right: 8px;
}
.user {
  padding-right: 8px;
}
.log-out {
  padding-right: 34px;
}
</style>
