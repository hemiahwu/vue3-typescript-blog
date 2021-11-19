<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>米修|博客</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">标题排序</button>
        <button @click="handleClick('salary')">薪资排序</button>
        <button @click="handleClick('location')">位置排序</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "@/types/Job";
import OrderTerm from "@/types/OrderTerm";
import JobList from "./components/JobList.vue";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "Web前端开发工程师",
        location: "北京",
        salary: 18000,
        id: "1",
      },
      {
        title: "Vue系前端开发工程师",
        location: "全国",
        salary: 20000,
        id: "2",
      },
      {
        title: "React系前端开发工程师",
        location: "全国",
        salary: 25000,
        id: "3",
      },
      {
        title: "Angular系前端开发工程师",
        location: "上海",
        salary: 17000,
        id: "4",
      },
      {
        title: "全栈开发工程师",
        location: "深圳",
        salary: 32000,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, order, handleClick };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
