<template>
  <div class="container">
    <div class="accordion">
      <the-accordion :fruit="tree.oranges" @my-choice="choise"></the-accordion>
      <the-accordion :fruit="tree.apple" @my-choice="choise"></the-accordion>
    </div>
    <p class="main__lable">{{ lable.lable }}</p>
  </div>
</template>

<script>
import TheAccordion from "@/TheAccordion";
import tree from "./tree"; // беру данные из внешнего обьекта
export default {
  components: { TheAccordion },
  data() {
    return {
      tree,
      lable: "",
    };
  },
  methods: {
    choise(data) {
      this.lable = data;
    },
  },
};
</script>
<style>
.main__lable {
  font-size: 30px;
  margin-right: 50px;
  align-self: center;
}
.container {
  display: flex;
  justify-content: space-between;
}
</style>
