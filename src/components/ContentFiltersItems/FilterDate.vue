<template>
  <div class="period-frames">
    <v-menu v-model="showCalendar" offset-y transition="slide-y-transition">
      <template v-slot:activator="{ on }">
        <v-text-field
          class="filter-frame period-date"
          v-model="formattedDate"
          v-on="on"
          hide-details
          solo
          dense
        ></v-text-field>
      </template>
      <v-date-picker
        v-model="date"
        @change="changeDate"
        no-title
      ></v-date-picker>
    </v-menu>

    <v-menu v-model="showTime" offset-y transition="slide-y-transition">
      <template v-slot:activator="{ on }">
        <v-text-field
          class="filter-frame period-time"
          v-model="time"
          @change="changeTime"
          v-on="on"
          hide-details
          solo
          dense
        ></v-text-field>
      </template>
      <v-time-picker v-model="time" format="24hr"></v-time-picker>
    </v-menu>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      showCalendar: false,
      showTime: false,
      date: new Date().toISOString().substr(0, 10),
      time: "00:00",
    };
  },
  props: {},
  computed: {
    formattedDate() {
      let dateArray: string[] = (this.date as string).split("-");
      const [year, month, day] = dateArray;
      return day + "." + month + "." + year;
    },
    fullDate() {
      let date = (this as any).formattedDate;
      let time = (this as any).time;
      return date + " " + time;
    },
  },
  methods: {
    changeDate() {
      this.$emit("change-date", (this as any).formattedDate);
    },
    changeTime() {
      this.$emit("change-time", (this as any).time);
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
::v-deep .v-text-field {
  font-size: 14px;
  z-index: 10;
  overflow: visible;
}
::v-deep div.v-input__slot {
  width: 96px !important;
  padding: 0 0 0 12px !important;
}
</style>
