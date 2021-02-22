<template>
  <div>
    <table class="table">
      <caption class="table__caption">
        {{
          tableTitle
        }}
      </caption>
      <colgroup>
        <col width="60" />
        <col width="60" />
      </colgroup>
      <thead>
        <tr>
          <th
            class="table__title"
            v-for="titleArray in titleArrays"
            v-bind:key="titleArray.index"
          >
            {{ titleArray.title }}
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pageData in pageDatas" v-bind:key="pageData.id">
          <td>{{ pageData.userId }}</td>
          <td>{{ pageData.id }}</td>
          <td>{{ pageData.title }}</td>
          <td>{{ pageData.body }}</td>
        </tr>
      </tbody>
    </table>
    <div class="pagination">
      <button
        type="button"
        v-bind:disabled="pageNumber === 0"
        class="pagination__button"
        v-on:click="movePrevPage"
      >
        {{ prevText }}
      </button>
      <button
        type="button"
        v-bind:disabled="pageNumber === endDataList"
        class="pagination__button"
        v-on:click="moveNextPage"
      >
        {{ nextText }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "pagination-list",
  data() {
    return {
      tableTitle: "(Vue.js) JSON Data 불러오기",
      prevText: "이전으로",
      nextText: "다음으로",
      pageNumber: 0,
      titleArrays: [
        { title: "userId" },
        { title: "Id" },
        { title: "title" },
        { title: "body" },
      ],
    };
  },
  props: {
    // 부모에게 가져온 JSON Data 리스트 배열 형태로 담아온다.
    listArray: {
      type: Array,
      required: true,
    },

    // 사용자 정의 기본값 (리스트 보여줄 갯수를 정의함)
    pageDefault: {
      type: Number,
      required: false,
      default: 10,
    },
  },
  methods: {
    // 버튼 클릭 시 pageNumber 숫자가 1 씩 줄어든다.
    movePrevPage() {
      this.pageNumber -= 1;
      console.log(this.pageNumber);
    },
    // 버튼 클릭 시 pageNumber 숫자가 1 씩 커진다.
    moveNextPage() {
      this.pageNumber += 1;
      console.log(this.pageNumber);
    },
  },
  // 필요에 따라 호출되도록 함수가 실행되도록 computed 사용
  computed: {
    pageDatas() {
      // 버튼을 클릭할 때마다 listArray가 보여지는 넘버가 달라지도록 실행
      // 초깃값 - startPage = 0, endPage = 10
      let startPage = this.pageNumber * this.pageDefault;
      let endPage = startPage + this.pageDefault;

      // listArray를 pageNubmer에 따라 잘라서 보여준다.
      return this.listArray.slice(startPage, endPage);
    },

    // 반올림 해서, (listArray의 총 길이 / 10) - 1 까지 보여주도록 한다.
    endDataList() {
      return Math.floor(this.listArray.length / 10 - 1);
    },
  },
};
</script>

<style>
</style>
