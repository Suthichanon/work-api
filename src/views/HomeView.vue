<template>
  <button @click="LoadUser()">โหลดข้อมูลอัตราแลกเปลี่ยนเหรียญ Crypto</button>
  <!-- <div>{{ UserData }}</div> -->    
  <ul>
    <li v-for="data,i in Data" :key="i">
    {{ data.symbol }} <br> {{ data.lastPrice }}
    </li>
  </ul>
</template>

<script setup lang="ts">
import axios from"axios";
import { ref } from "vue";
const Data = ref([]);
const url = ref("https://data.binance.com/api/v3/ticker/24hr")
function LoadUser() {
    axios
    .get(url.value)
    .then((Response)=>{
        Data.value = Response.data;
    })
    .catch((err) => {
        console.log(err);
    })
}
</script>

<style scoped>
ul{
  border: 1px solid red;
  padding-left: 40px;
}
ul li{
  border: 1px solid rgb(0, 0, 0);
  list-style: none;
}
</style>
