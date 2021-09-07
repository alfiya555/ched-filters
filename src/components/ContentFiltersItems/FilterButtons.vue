<template>
  <div class="filter-buttons">
    <!-- Настройки/сбросить/найти (фильтр) -->
    <div class="filter-buttons__element filter-settings">
      <v-btn class="filter-settings" @click="showFilterRows" text block>
        <img src="../../assets/Filter.png" />
      </v-btn>
    </div>
    <div class="filter-buttons__element reset">
      <v-btn @click="resetForm" class="reset" elevation="0" text block>
        Сбросить
      </v-btn>
    </div>
    <div class="filter-buttons__element submit">
      <v-btn class="submit" text block type="submit"> Найти </v-btn>
    </div>
    <!-- <button type="submit" class="filter-buttons__element submit">
      Найти
    </button> -->
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {};
  },
  methods: {
    showFilterRows: function () {
      this.$emit("show-filters");
    },
    resetForm: function () {
      this.$emit("reset-form");
    },
    submitForm: function () {
      this.$emit("submit-form");
    },
  },
});
</script>

<style scoped>
.filter-buttons {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-end;
}
.filter-buttons {
  flex: 1;
  justify-content: flex-end;
}
.filter-buttons__element {
  height: 40px;
  border: 1px solid #2462d1;
  border-radius: 4px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
  margin-left: 8px;
}
.filter-settings {
  width: 40px;
}
.reset {
  width: 116px;
  font-family: Golos;
  font-weight: 500;
  font-size: 14px;
  color: #2462d1 !important;
  text-transform: none;
  letter-spacing: 0;
}
.submit {
  width: 116px;
  background: #2462d1;
  font-family: Golos;
  font-weight: 500;
  font-size: 14px;
  color: #ffffff !important;
  text-transform: none;
  letter-spacing: 0;
}
</style>
