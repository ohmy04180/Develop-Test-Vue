<template>
  <div>
    <!-- HTML에서는 CamelCale가 적용이 안되므로, Kebap-Cas로 작성 -->
    <pagination-list v-bind:list-array = "dataArrays"></pagination-list>
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
        // 해당 JSON Data를 dataArrays 배열에 담아준다.
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