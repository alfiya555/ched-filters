<template>
  <div>
    <v-form
      ref="form"
      id="filterForm"
      class="filter-form"
      @submit.prevent="submitForm"
    >
      <div class="filter-row1">
        <FilterSelect
          v-model="type"
          :items="itemsType"
          :name="'Тип'"
          :maxNumber="3"
          class="type-source-width"
        />
        <div class="filter-period">
          <div class="filter-name">Период</div>
          <div class="period-frames">
            <FilterDate
              @change-date="changeDateFrom"
              @change-time="changeTimeFrom"
            />
            <div class="period-tire">&mdash;</div>
            <FilterDate
              @change-date="changeDateTo"
              @change-time="changeTimeTo"
            />
          </div>
        </div>
        <FilterButtons @show-filters="showFilters" @reset-form="resetForm" />
      </div>
      <div class="filter-row2" id="filter-row2">
        <FilterSelect
          v-model="source"
          :items="itemsSource"
          :name="'Источник'"
          :maxNumber="3"
          class="type-source-width"
        />
        <FilterSelect
          v-model="user"
          :items="itemsUser"
          :name="'Пользователь'"
          :maxNumber="1"
          class="user-category-width"
        />
        <FilterSelect
          v-model="category"
          :items="itemsCategory"
          :name="'Категория'"
          :maxNumber="1"
          class="user-category-width"
        />
      </div>
      <div class="filter-row3" id="filter-row3">
        <FilterTextField v-model="description" :name="'Описание'" />
        <FilterTextField v-model="object" :name="'Объект'" />
      </div>
    </v-form>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import FilterButtons from "./ContentFiltersItems/FilterButtons.vue";
import FilterSelect from "./ContentFiltersItems/FilterSelect.vue";
import FilterTextField from "./ContentFiltersItems/FilterTextField.vue";
import FilterDate from "./ContentFiltersItems/FilterDate.vue";

export default Vue.extend({
  data() {
    return {
      type: [],
      dateFrom: (this as any).formattedDate(
        new Date().toISOString().substr(0, 10)
      ),
      timeFrom: "00:00",
      dateTo: (this as any).formattedDate(
        new Date().toISOString().substr(0, 10)
      ),
      timeTo: "00:00",
      source: [],
      user: [],
      category: [],
      description: "",
      object: "",
      itemsType: [
        "Ошибка",
        "Сообщение",
        "Тип1",
        "Тип2",
        "Тип3",
        "Тип4",
        "Тип5",
      ],
      itemsSource: ["ППиО", "Ист1", "Ист2", "Ист3", "Ист4", "Ист5", "Ист6"],
      itemsUser: [
        "Без пользователя",
        "User1",
        "User2",
        "User3",
        "User4",
        "User5",
        "User6",
      ],
      itemsCategory: [
        "Получение ТК",
        "Обработка ТК",
        "Категория 1",
        "Категория 2",
        "Категория 3",
        "Категория 4",
        "Категория 5",
      ],
    };
  },
  components: {
    FilterButtons,
    FilterSelect,
    FilterTextField,
    FilterDate,
  },
  methods: {
    showFilters: function () {
      let row2 = document.getElementById("filter-row2");
      let row3 = document.getElementById("filter-row3");
      this.showAndHideRow(row2);
      this.showAndHideRow(row3);
    },
    showAndHideRow(row: HTMLElement | null) {
      if (row) {
        if (row.style.display === "none") {
          row.style.display = "flex";
        } else {
          row.style.display = "none";
        }
      }
    },
    resetForm() {
      if (this.$refs.form) {
        (this.$refs as any).form.reset();
      }
    },
    submitForm(e: any) {
      this.$emit("filter-table", {
        type: this.type,
        dateFrom: (this as any).dateFrom + " " + (this as any).timeFrom,
        dateTo: (this as any).dateTo + " " + (this as any).timeTo,
        source: this.source,
        user: this.user,
        category: this.category,
        description: this.description,
        object: this.object,
      });
    },
    changeDateFrom(newDate: string) {
      this.dateFrom = newDate;
    },
    changeDateTo(newDate: string) {
      this.dateTo = newDate;
    },
    changeTimeFrom(newTime: string) {
      this.timeFrom = newTime;
    },
    changeTimeTo(newTime: string) {
      this.timeTo = newTime;
    },
    formattedDate(date: string): string {
      let dateArray: string[] = (date as string).split("-");
      const [year, month, day] = dateArray;
      return day + "." + month + "." + year;
    },
  },
});
</script>

<style>
.type-source-width {
  width: 413px !important;
  min-width: 413px;
  max-width: 413px;
}
.user-category-width {
  width: 346px;
  max-width: 346px;
}
.filter-form {
  margin: 0;
  height: 100%;
  width: 1120px !important;
  box-sizing: border-box !important;
}
.filter-select {
  width: 100%;
  box-sizing: border-box;
  height: 40px;
}
.filter-row1 {
  display: flex;
  flex-direction: row;
  justify-content: space-between !important;
  align-items: flex-end;
  width: 100%;
}
.filter-row2 {
  display: none;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-end;
  margin-top: 38px;
}
.filter-row3 {
  display: none;
  flex-direction: row;
  justify-content: flex-start;
  align-items: flex-end;
}
.filter-name {
  font-family: "YS Text";
  font-style: normal;
  font-weight: normal;
  font-size: 14px;
  margin-top: 16px;
}
.filter-frame {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  background: #ffffff;
  border: 1px solid #d9d9de;
  box-sizing: border-box;
  border-radius: 4px;
  height: 40px;
  position: relative;
}
.subframe {
  font-family: Golos;
  font-size: 14px;
  background: rgba(217, 217, 222, 0.7);
  border-radius: 2px;
  height: 32px;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  margin: 4px 0 4px 4px;
  padding-left: 4px;
}
.text_grey {
  font-family: Golos;
  font-size: 14px;
  color: black;
  padding-left: 12px;
}
.filter-period {
  margin-left: 8px;
  flex: 1;
}
.period-tire {
  margin-right: 8px;
  font-weight: bold;
}
.period-frames {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  font-family: Golos;
  font-size: 10px;
}
</style>
