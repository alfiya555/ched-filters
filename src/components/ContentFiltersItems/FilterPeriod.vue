<template>
  <div class="filter-period">
    <!-- Период (фильтр) -->
    <div class="filter-name">Период</div>
    <div class="period-frames" id="periodFrames">
      <v-menu
        v-model="showCalendarFrom"
        offset-y
        transition="slide-y-transition"
      >
        <template v-slot:activator="{ on }">
          <v-text-field
            class="filter-frame period-date"
            v-model="formattedDateFrom"
            v-on="on"
            hide-details
            solo
            dense
          ></v-text-field>
        </template>
        <v-date-picker v-model="dateFrom" no-title></v-date-picker>
      </v-menu>

      <v-menu v-model="showTimeFrom" offset-y transition="slide-y-transition">
        <template v-slot:activator="{ on }">
          <v-text-field
            class="filter-frame period-time"
            v-model="timeFrom"
            v-on="on"
            hide-details
            solo
            dense
          ></v-text-field>
        </template>
        <v-time-picker v-model="timeFrom" format="24hr"></v-time-picker>
      </v-menu>

      <div class="period-tire">&mdash;</div>

      <v-menu v-model="showCalendarTo" offset-y transition="slide-y-transition">
        <template v-slot:activator="{ on }">
          <v-text-field
            class="filter-frame period-date"
            v-model="formattedDateTo"
            v-on="on"
            hide-details
            solo
            dense
          ></v-text-field>
        </template>
        <v-date-picker v-model="dateTo" no-title></v-date-picker>
      </v-menu>

      <v-menu v-model="showTimeTo" offset-y transition="slide-y-transition">
        <template v-slot:activator="{ on }">
          <v-text-field
            class="filter-frame period-time"
            v-model="timeTo"
            v-on="on"
            hide-details
            solo
            dense
          ></v-text-field>
        </template>
        <v-time-picker v-model="timeTo" format="24hr"></v-time-picker>
      </v-menu>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      showCalendarFrom: false,
      showCalendarTo: false,
      showTimeFrom: false,
      showTimeTo: false,
      dateFrom: new Date().toISOString().substr(0, 10),
      dateTo: new Date().toISOString().substr(0, 10),
      timeFrom: "00:00",
      timeTo: "00:00",
    };
  },
  computed: {
    formattedDateFrom() {
      let dateArray: string[] = this.dateFrom.split("-");
      const [year, month, day] = dateArray;
      return day + "." + month + "." + year;
    },
    formattedDateTo() {
      let dateArray: string[] = this.dateTo.split("-");
      const [year, month, day] = dateArray;
      return day + "." + month + "." + year;
    },
  },
});
</script>

<style scoped>
.filter-period {
  margin-left: 8px;
  flex: 1;
}
.period-frames {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  font-family: Golos;
  font-size: 10px;
}
.period-date {
  width: 96px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  overflow: hidden !important;
}
.period-time {
  width: 80px;
  margin: 0 8px 0 8px !important;
  display: flex;
  flex-direction: row;
  justify-content: center;
  overflow: hidden !important;
}
.period-tire {
  margin-right: 8px;
  font-weight: bold;
}
::v-deep .v-text-field {
  font-size: 14px;
  z-index: 10;
  overflow: visible;
}
::v-deep .v-input__slot {
  width: 96px !important;
}
</style>
