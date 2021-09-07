<template>
  <v-app>
    <div class="wrapper">
      <Header />
      <div class="main-wrapper">
        <LeftMenu />
        <div class="main-content-wrapper">
          <div class="main-content">
            <ContentHeader />
            <ContentFilters @filter-table="getFilterObject" />
            <ContentTable :filterObject="filterObject" />
          </div>
        </div>
      </div>
    </div>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";
import ContentFilters from "./components/ContentFilters.vue";
import ContentHeader from "./components/ContentHeader.vue";
import ContentTable from "./components/ContentTable.vue";
import Header from "./components/Header.vue";
import LeftMenu from "./components/LeftMenu.vue";

export default Vue.extend({
  name: "App",

  components: {
    ContentFilters,
    ContentHeader,
    ContentTable,
    Header,
    LeftMenu,
  },

  data() {
    return {
      filterObject: {
        type: [],
        dateFrom: "",
        dateTo: "",
        source: [],
        user: [],
        category: [],
        description: "",
        object: "",
      },
    };
  },
  methods: {
    getFilterObject(obj: {
      type: [];
      dateFrom: "";
      dateTo: "";
      source: [];
      user: [];
      category: [];
      description: "";
      object: "";
    }) {
      this.filterObject = obj;
    },
  },
});
</script>

<style>
@font-face {
  font-family: "Golos";
  src: url("assets/font/Golos-Text_Regular.css");
  src: url("assets/font/Golos-Text_Regular.woff") format("woff");
  src: url("assets/font/Golos-Text_Regular.woff2") format("woff2");
}
@font-face {
  font-family: "YS Text";
  src: url("assets/font/YandexSansText-Regular.css");
  src: url("assets/font/YandexSansText-Regular.woff") format("woff");
  src: url("assets/font/YandexSansText-Regular.woff2") format("woff2");
}
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  font-family: Golos !important;
}
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  flex: 1;
  width: 100%;
  height: 100%;
}
.main-wrapper {
  display: flex;
  flex-direction: row;
  height: 100%;
  width: 100%;
  flex: 1;
}
.main-content-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: center;
  background-color: #f5f5f7;
  margin-left: 64px;
  flex: 1;
  width: 100%;
  height: 100%;
}
.main-content {
  width: 1120px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
}
</style>
