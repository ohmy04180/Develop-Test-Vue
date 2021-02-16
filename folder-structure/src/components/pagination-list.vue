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
        <tr v-for="list in lists" v-bind:key="list.id">
          <td>{{ list.userId }}</td>
          <td>{{ list.id }}</td>
          <td>{{ list.title }}</td>
          <td>{{ list.body }}</td>
        </tr>
      </tbody>
    </table>
    <ul class="pagination">
      <li v-for="(list, index) in lists" v-bind:key="list.id">
        <button type="button" v-on:click.prevent="doSomething">
          {{ index + 1 }}
        </button>
      </li>
    </ul>
    <!-- <button v-on:click="fetchData">데이터 가져오기</button> -->
  </div>
</template>

<script>
export default {
  name: "pagination-list",
  data() {
    return {
      tableTitle: "JSON Data 불러오기",
      lists: [
        { userId: 1, id: 1, title: "hoho", body: "hihi" },
        { userId: 1, id: 2, title: "hoho", body: "hihi" },
        { userId: 1, id: 3, title: "hoho", body: "hihi" },
      ],
      dataArray: [],
    };
  },
  methods: {
    doSomething() {
      alert("click");
    },
  },
};
</script>

<style>
@charset "UTF-8";
html,
body,
div,
span,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
abbr,
address,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
samp,
small,
strong,
sub,
sup,
var,
b,
i,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}

sup {
  vertical-align: super;
}

sub {
  vertical-align: sub;
}

ol,
ul {
  list-style: none;
}

blockquote,
q {
  quotes: none;
}

em {
  font-style: normal;
}

blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}

a:focus,
button:focus,
input:focus {
  outline: 0;
}

* {
  box-sizing: border-box;
}

body {
  font-family: "NotoSansKR", "メイリオ", Meiryo, "Yu Gothic UI",
    "Microsoft YaHei UI", "Microsoft JhengHei UI", -apple-system,
    BlinkMacSystemFont, "Segoe UI", "Open Sans", "Helvetica Neue", sans-serif;
}

code {
  font-family: Consolas, Menlo, "SFMono-Regular", Courier, monospace;
}

strong {
  font-weight: 700;
}

.hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
  visibility: visible;
  white-space: nowrap;
}

.ir-pm {
  /* 레이아웃에 영향을 끼치지 않도록 */
  position: absolute;
  /* 스크린 리더가 읽을 수 있도록 */
  width: 1px;
  height: 1px;
  /* 눈에 보이는 부분을 제거 */
  clip: rect(0 0 0 0);
  margin: -1px;
  overflow: hidden;
}

.img-g {
  display: block;
  width: 100%;
}

.caption-out {
  width: 0;
  height: 0;
  padding: 0;
  margin: 0;
  visibility: hidden;
}

.filter-highlight {
  background-color: #fff09c;
}

body {
  width: 1180px;
  margin: 50px auto;
}

.table {
  width: 400px;
  margin: 0 auto;
  border: 1px solid #ccc;
}

.table__caption {
  margin-bottom: 8px;
  font-size: 16px;
  font-weight: 400;
  text-align: center;
  color: #666;
}

.table table {
  width: 100%;
  border: 1px solid #ccc;
}

.table th,
.table td {
  padding: 4px;
  vertical-align: middle;
  word-break: break-all;
}

.table th {
  font-size: 15px;
  font-weight: 500;
  border-bottom: 1px solid #ccc;
}

.table td {
  font-size: 14px;
  font-weight: 400;
  text-align: left;
  border-bottom: 1px solid #ccc;
}

th + th,
td + td {
  border-left: 1px solid #ccc;
}

.table tr:hover td {
  background-color: #fafafa;
}

.pagination {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  margin-top: 16px;
}

.pagination__list {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.pagination__text {
  display: block;
  padding: 0 4px;
}

.pagination__button {
  text-decoration: none;
}

.pagination__button {
  border: none;
}

.pagination__button {
  display: block;
  height: 30px;
  line-height: 30px;
  padding: 0 16px;
  background-color: transparent;
  border-radius: 5px;
  font-size: 16px;
  text-align: center;
  cursor: pointer;
  color: #666;
}
.pagination__button:hover {
  background-color: #fafafa;
}
.pagination__button:active {
  background-color: #f0f0f0;
}
</style>
