<template>
  <div class="filter-select">
    <div class="filter-name">{{ name }}</div>
    <div class="filter-frame filter-select-frame">
      <v-select
        class="filter-select"
        :value="value"
        @change="changeEvent"
        :items="items"
        chips
        dense
        solo
        flat
        multiple
      >
        <template
          v-slot:selection="{ item, index }"
          class="filter-frame subframes"
        >
          <v-chip
            v-if="index >= 0 && index < maxNumber"
            class="subframe"
            close
            @click:close="remove(index)"
          >
            <span>{{ item }}</span>
          </v-chip>
          <span v-if="index === maxNumber" class="grey--text text-caption">
            (Ещё +{{ value.length - maxNumber }})
          </span>
        </template>
      </v-select>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  props: {
    value: {
      type: Array,
      default: () => [],
    },
    name: {
      type: String,
    },
    items: {
      type: Array,
      default: () => [],
    },
    maxNumber: {
      type: Number,
    },
  },
  data() {
    return {};
  },
  model: {
    prop: "value",
    event: "change",
  },
  methods: {
    remove(index: number) {
      this.value.splice(index, 1);
    },
    changeEvent(e: any) {
      this.$emit("change", e);
    },
  },
});
</script>

<style scoped>
.filter-select {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-start;
}
.filter-select-frame {
  width: 100%;
  position: relative;
  box-sizing: border-box;
}
.type-frame {
  width: 100%;
  z-index: 1;
  position: absolute;
  box-sizing: border-box;
}
::v-deep .v-chip {
  font-size: 14px;
  background: rgba(217, 217, 222, 0.7) !important;
  border-radius: 2px !important;
  height: 32px;
  margin: 4px 4px 4px 0 !important;
  padding-left: 12px;
}
::v-deep button.v-chip__close {
  color: #a7a7ab;
}
::v-deep div.v-input__slot {
  padding: 0 0 0 4px !important;
}
::v-deep div.v-select {
  border: 1px solid #d9d9de;
  border-radius: 4px;
}
</style>
