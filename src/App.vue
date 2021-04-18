<template>
  <the-accordion :fruit="tree.oranges"></the-accordion>
  <the-accordion :fruit="tree.apple"></the-accordion>
</template>

<script>
import TheAccordion from "@/TheAccordion";
import tree from "./tree"; // беру данные из внешнего обьекта
export default {
  components: { TheAccordion },
  data() {
    return {
      tree,
    };
  },
};
</script>
