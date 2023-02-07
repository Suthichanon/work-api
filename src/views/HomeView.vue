
<template>
  <button @click="loadData()">Load Crypto Exchange Rates</button>
  <ul>
    <li v-for="data, i in Data" :key="i">
      {{ data.symbol }} <br> {{ data.lastPrice }}
    </li>
  </ul>
</template>


<script lang="ts">
import axios from "axios";
import { ref } from "vue";
export default {
  setup() {
    const Data = ref([]);

    function loadData() {
      const url = "https://data.binance.com/api/v3/ticker/24hr";

      axios.get(url)
        .then(response => {
          Data.value = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    }

    return {
      Data,
      loadData
    };
  }
};
</script>

<style scoped>
ul {
  border: 1px solid red;
  padding-left: 40px;
}

ul li {
  border: 1px solid black;
  list-style: none;
}
</style>