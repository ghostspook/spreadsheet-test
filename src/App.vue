<template>
  <div id="app">
    <vue-table
      v-model="products"
      :headers="headers"
      :custom-options="customOptions"
      :style-wrap-vue-table="styleWrapVueTable"
      :disable-cells="disableCells"
      :disable-sort-thead="disableSortThead"
      :loading="loading"
      :parent-scroll-element="parentScrollElement"
      :select-position="selectPosition"
      :submenu-tbody="submenuTbody"
      :submenu-thead="submenuThead"
      @tbody-checked-row="checkedData"
      @tbody-all-checked-row="checkedAllData"
      @tbody-change-data="changeData"
      @tbody-submenu-click-change-color="changeColorTbody"
      @tbody-submenu-click-change-value="changeValueTbody"
      @thead-submenu-click-change-color="changeColorThead"
      @thead-submenu-click-change-value="changeValueThead"
      @thead-td-sort="sortProduct"
    >
      <div slot="header">Specific Header</div>
      <div slot="loader">Loader</div>
    </vue-table>
  </div>
</template>

<script>
import VueTable from "vuejs-spreadsheet";
import exempleData from "./data";

export default {
  name: "VueSpreadsheet",
  data() {
    return exempleData;
  },
  components: {
    VueTable,
  },
  mounted() {
    this.loading = true;
    setTimeout(() => {
      this.loading = false;
    }, 300);
  },
  methods: {
    checkedAllData(isChecked) {
      console.log("checked all data", isChecked);
    },
    checkedData(row) {
      console.log("checked data", row);
    },
    changeData(row, header) {
      console.log(row, header);
    },
    sortProduct(event, header, colIndex) {
      console.log("sort product");
    },
    // callback
    changeColorThead(event, header, colIndex) {
      this.headers[colIndex].style.color = "#e40000";
    },
    changeValueThead(event, header, colIndex) {
      this.headers[colIndex].headerName = "T-shirt";
    },
    changeColorTbody(event, header, rowIndex, colIndex) {
      this.products[rowIndex][header].style = {};
      this.products[rowIndex][header].style.color = "#e40000";
    },
    changeValueTbody(event, header, rowIndex, colIndex) {
      this.products[rowIndex][header].value = "T-shirt";
    },
  },
};
</script>


