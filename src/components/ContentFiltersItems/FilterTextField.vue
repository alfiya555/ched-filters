<template>
  <div class="filter-text-field">
    <div class="filter-name">{{ name }}</div>
    <div>
      <v-text-field
        v-if="name === 'Объект'"
        :value="value"
        @change="changeEvent"
        class="text_grey"
        placeholder="Не задан"
        solo
        flat
        dense
      ></v-text-field>
      <v-text-field
        v-else
        :value="value"
        @change="changeEvent"
        class="text_grey"
        placeholder="Не задано"
        solo
        flat
        dense
      ></v-text-field>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  props: {
    name: {
      type: String,
    },
    value: {
      type: String,
    },
  },
  model: {
    prop: "value",
    event: "change",
  },
  methods: {
    changeEvent(e: any) {
      this.$emit("change", e);
    },
  },
});
</script>

<style scoped>
.filter-text-field {
  width: 240px;
  margin-right: 8px;
}
::v-deep .v-input__slot {
  border: 1px solid #d9d9de !important;
  border-radius: 4px;
}
</style>
