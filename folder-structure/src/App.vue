<template>
  <div>
    <pagination-list :list-array = "dataArrays"></pagination-list>
    <!-- <button v-on:click="fetchData">데이터 가져오기</button> -->
  </div>
</template>

<script>
import axios from "axios";
import PaginationList from "./components/pagination-list";

export default {
  name: "app",
  components: {
    PaginationList,
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then((response) => {
        console.log(response);
        console.log(typeof response.data);
        this.dataArrays = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
  data() {
    return {
      dataArrays: []
    };
  },
  methods: {
  },
};
</script>

<style>
@import "./App.scss";
</style>