<template>
  <div>
    <table class="table">
      <caption class="table__caption">
        {{
          tableTitle
        }}
      </caption>
      <thead>
        <tr>
          <th class="table__title">UserId</th>
          <th class="table__title">Id</th>
          <th class="table__title">Text</th>
          <th class="table__title">Body</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in listArray" v-bind:key="item.id">
          <td>{{ item.userId }}</td>
          <td>{{ item.id }}</td>
          <td>{{ item.title }}</td>
          <td>{{ item.body }}</td>
        </tr>
      </tbody>
    </table>
    <div class="pagination">
      <button type="button" class="pagination__button">
        {{ prevText }}
      </button>
      <button type="button" class="pagination__button">
        {{ nextText }}
      </button>
    </div>
    <button v-on:click="test">데이터 가져오기</button>
  </div>
</template>

<script>
 export default {
  name: "pagination-list",
  data() {
    return {
      tableTitle: "JSON Data 불러오기",
      prevText:"이전으로",
      nextText:"다음으로",
      dataArrays: []
    };
  },
  props: {
    listArray: {
      type: Array,
      required: true
    },

  },
  methods: {
    doSomething() {
      alert("click");
    },
    test(){
      console.log(this.listArray);
    }
  },
};
</script>

<style>
</style>
