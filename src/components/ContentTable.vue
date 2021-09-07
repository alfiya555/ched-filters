<template>
  <div class="data-table">
    <v-data-table
      v-model="selected"
      :headers="headersItems"
      :items="rowItems"
      item-key="id"
      :sort-by="[]"
      :sort-desc="[false, true]"
      multi-sort
      show-select
    >
    </v-data-table>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      selected: [],
      rowItems: [
        {
          id: 0,
          type: "Ошибка",
          date: "12.06.2021 00:00",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 1,
          type: "Сообщение",
          date: "12.06.2021 00:00",
          source: "Ист1",
          category: "Обработка ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 2,
          type: "Ошибка",
          date: "12.06.2021 00:02",
          source: "ППиО",
          category: "Получение ТК",
          description: "Текст записи в журнале системных событий",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 3,
          type: "Сообщение",
          date: "12.06.2021 00:03",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 4,
          type: "Сообщение",
          date: "12.06.2021 00:04",
          source: "Ист2",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 5,
          type: "Тип1",
          date: "12.06.2021 00:05",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "User1",
        },
        {
          id: 6,
          type: "Тип1",
          date: "12.06.2021 00:06",
          source: "ППиО",
          category: "Обработка ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "User2",
        },
        {
          id: 7,
          type: "Тип2",
          date: "12.06.2021 00:07",
          source: "Ист3",
          category: "Получение ТК",
          description: "Текст записи в журнале системных событий",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 8,
          type: "Тип2",
          date: "12.06.2021 00:08",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "User4",
        },
        {
          id: 9,
          type: "Тип3",
          date: "12.06.2021 00:09",
          source: "Ист4",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-37373",
          user: "Без пользователя",
        },
        {
          id: 10,
          type: "Сообщение",
          date: "12.06.2021 00:10",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-55555",
          user: "Без пользователя",
        },
        {
          id: 11,
          type: "Тип1",
          date: "12.06.2021 00:11",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-55555",
          user: "User1",
        },
        {
          id: 12,
          type: "Тип1",
          date: "12.06.2021 00:12",
          source: "ППиО",
          category: "Обработка ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-55555",
          user: "User2",
        },
        {
          id: 13,
          type: "Тип2",
          date: "12.06.2021 00:13",
          source: "ППиО",
          category: "Получение ТК",
          description: "Текст записи в журнале системных событий",
          object: "9345-3635-3636-55555",
          user: "Без пользователя",
        },
        {
          id: 14,
          type: "Тип2",
          date: "12.06.2021 00:10",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-55555",
          user: "User4",
        },
        {
          id: 15,
          type: "Тип3",
          date: "12.06.2021 00:11",
          source: "ППиО",
          category: "Получение ТК",
          description: "Ошибка проверки метаданных",
          object: "9345-3635-3636-55555",
          user: "Без пользователя",
        },
      ],
    };
  },
  methods: {
    dateParse(str: string) {
      let fullDateAndTime = str.split(" ");
      let fullDate = fullDateAndTime[0].split(".");
      let fullTime = fullDateAndTime[1].split(":");
      let date = fullDate[0] as any;
      let month = (fullDate[1] as any) - 1;
      let year = fullDate[2] as any;
      let hours = fullTime[0] as any;
      let min = fullTime[1] as any;
      let messageDate = new Date(year, month, date, hours, min);
      return messageDate.getTime();
    },
  },
  computed: {
    headersItems() {
      return [
        {
          text: "Тип",
          value: "type",
          class: "table-head",
          filter: (value: string) => {
            if ((this as any).filterObject.type.length === 0) {
              return true;
            }
            return (this as any).filterObject.type.includes(value);
          },
        },
        {
          text: "Дата",
          value: "date",
          class: "table-head",
          filter: (value: string) => {
            if (
              (this.filterObject as any).dateFrom ===
              (this.filterObject as any).dateTo
            ) {
              return true;
            }
            return (
              (this as any).dateParse(this.filterObject.dateFrom) <=
                (this as any).dateParse(value) &&
              (this as any).dateParse(this.filterObject.dateTo) >=
                (this as any).dateParse(value)
            );
          },
        },
        {
          text: "Источник",
          value: "source",
          class: "table-head",
          filter: (value: string) => {
            if ((this.filterObject as any).source.length === 0) {
              return true;
            }
            return (this as any).filterObject.source.includes(value);
          },
        },
        {
          text: "Категория",
          value: "category",
          class: "table-head",
          filter: (value: string) => {
            if ((this.filterObject as any).category.length === 0) {
              return true;
            }
            return (this as any).filterObject.category.includes(value);
          },
        },
        {
          text: "Описание",
          value: "description",
          class: "table-head",
          filter: (value: string) => {
            console.log((this.filterObject as any).description);
            if (!(this.filterObject as any).description) {
              return true;
            }
            return (
              value
                .toUpperCase()
                .indexOf(
                  (this as any).filterObject.description.toUpperCase()
                ) !== -1
            );
          },
        },
        {
          text: "Объект",
          value: "object",
          class: "table-head",
          filter: (value: string) => {
            console.log((this.filterObject as any).object);
            if (!(this.filterObject as any).object) {
              return true;
            }
            return (
              value
                .toUpperCase()
                .indexOf((this as any).filterObject.object.toUpperCase()) !== -1
            );
          },
        },
        {
          text: "Пользователь",
          value: "user",
          class: "table-head",
          filter: (value: string) => {
            if ((this.filterObject as any).user.length === 0) {
              return true;
            }
            return (this as any).filterObject.user.includes(value);
          },
        },
      ];
    },
  },
  props: {
    filterObject: {
      default: () => {
        return {
          type: [],
          dateFrom: "",
          dateTo: "",
          source: [],
          user: [],
          category: [],
          description: "",
          object: "",
        };
      },
    },
  },
});
</script>

<style scoped>
.data-table {
  width: 1120px;
  margin-top: 32px;
  border-radius: 8px 8px 0px 0px;
  overflow: hidden;
}
table {
  width: 100%;
  border-radius: 8px 8px 0px 0px;
  border-collapse: collapse;
  text-align: left;
}
.table-head {
  height: 40px;
  text-transform: uppercase;
  font-family: Golos;
  font-weight: 500;
  font-size: 10px;
  line-height: 16px;
  letter-spacing: 0.08em;
}
.table-head-div {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}
.table-head-arrow {
  margin: 0 5px;
}
::v-deep .v-data-table-header th {
  background-color: #ededf1 !important;
  text-transform: uppercase;
  height: 40px;
  font-weight: 500 !important;
  font-size: 10px;
  color: #21201f !important;
  line-height: 16px;
  letter-spacing: 0.08em;
}
::v-deep .v-data-table-body td {
  background-color: red !important;
}
</style>
