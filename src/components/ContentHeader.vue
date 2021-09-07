<template>
  <div class="content-header-wrapper">
    <div class="content-path">Главная / Администрирование / Журнал событий</div>
    <div class="content-header">
      <div class="event-log">Журнал событий</div>
      <div class="export">
        <v-menu style="width: 100%" open-on-hover bottom offset-y>
          <template v-slot:activator="{ on }">
            <v-btn v-on="on" text block>
              <img src="../assets/Download.png" /><span class="export-text"
                >Экспорт...</span
              >
            </v-btn>
          </template>
          <v-list>
            <v-list-item>CSW</v-list-item>
            <v-list-item>PDF</v-list-item>
          </v-list>
        </v-menu>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({});
</script>

<style scoped>
.content-header-wrapper {
  width: 100%;
}
.content-path {
  font-family: "Golos";
  font-weight: 400;
  font-size: 14px;
  color: #a7a7ab;
  padding-top: 16px;
  width: 100%;
}
.content-header {
  padding-top: 16px;
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}
.event-log {
  font-family: Golos;
  font-weight: 500;
  font-size: 32px;
  color: #21211f;
  flex: 1;
}
.export {
  max-width: 142px;
  height: 40px;
  border: 1px solid #2462d1;
  border-radius: 4px;
  align-self: flex-end;
  flex: 1;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
}
.export-text {
  padding-left: 9px;
  font-family: Golos;
  font-weight: 500;
  font-size: 14px;
  color: #2462d1;
  text-transform: none;
  letter-spacing: normal;
}
</style>
