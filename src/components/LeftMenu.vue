<template>
  <div class="menu-wrapper">
    <!-- Оболочка для левого меню -->
    <div class="menu-up">
      <!-- Верхняя часть меню -->
      <div class="menu-up__item blank-div"></div>
      <div class="menu-up__item">
        <v-btn icon tile><img src="../assets/1.Vector.png" /></v-btn>
      </div>
      <div class="menu-up__item">
        <v-btn icon tile><img src="../assets/2.Vector.png" /></v-btn>
      </div>
      <div class="menu-up__item">
        <v-btn icon tile><img src="../assets/3.Vector.png" /></v-btn>
      </div>
      <div class="menu-up__item">
        <v-btn icon tile><img src="../assets/4.Vector.png" /></v-btn>
      </div>
      <div class="menu-up__item">
        <v-btn icon tile><img src="../assets/5.Vector.png" /></v-btn>
      </div>
    </div>
    <div class="menu-down">
      <!-- Нижняя часть меню -->
      <div class="menu-down__item">
        <v-btn icon tile><img src="../assets/6.Vector.png" /></v-btn>
      </div>
      <div class="menu-down__item">
        <v-btn icon tile><img src="../assets/7.Vector.png" /></v-btn>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({});
</script>

<style scoped>
.menu-wrapper {
  width: 64px;
  display: flex;
  flex-direction: column;
  min-width: 64px;
  height: 100vh;
  background: #ffffff;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 99;
}
.menu-up {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  flex: 1;
}
.menu-up__item {
  padding-top: 31px;
}
.blank-div {
  height: 64px;
  max-height: 64px;
  margin: 0;
  padding: 0;
}
.menu-down {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: center;
  flex: 1;
}
.menu-down__item {
  padding-bottom: 22.4px;
}
</style>
