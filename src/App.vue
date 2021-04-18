<template>
  <the-accordion :fruit="tree.oranges" @my-choice="choise"></the-accordion>
  <the-accordion :fruit="tree.apple" @my-choice="choise"></the-accordion>
  <p class="main__lable">{{lable.lable}}</p>
</template>

<script>
import TheAccordion from "@/TheAccordion";
import tree from "./tree"; // беру данные из внешнего обьекта
export default {
  components: { TheAccordion },
  data() {
    return {
      tree,
      lable:""
    };
  },
  methods:{
    choise(data){
      this.lable = data
    }
  }
};
</script>
<style>
.main__lable{
  font-size: 250%;
  text-align: center;
}
</style>
