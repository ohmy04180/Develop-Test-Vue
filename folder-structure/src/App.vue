<template>
  <div>
    <!-- pagination-list 컴포넌트 불러옴 -->
    <!-- HTML에서는 CamelCale가 적용이 안되므로, Kebap-Case로 작성 -->
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
  // 인스턴스가 생성된 후 해당 데이터 불러온다.
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      // 프라미스 형태 (.then)
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