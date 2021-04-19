<template>
  <div class="main__container">
    <!--      название фрукта и при клике открываю страну-->
    <p class="main__fruit" @click="isActive = !isActive">{{ fruit.title }}</p>
    <!--        показываю если кликнул-->
    <div class="country__container">
      <div
        v-show="isActive"
        class="main__country"
        v-for="country in fruit.country"
        :key="country.title"
        @click="country.items.hide = !country.items.hide"
      >
        <!--        country.items.hide = !country.items.hide - изменяю внутренее свойство обьекта-->
        {{ country.title }}
        <the-country-item :country="country" :fruit="fruit"></the-country-item>
      </div>
    </div>
  </div>
</template>

<script>
import TheCountryItem from "@/TheCountryItem";
export default {
  components: { TheCountryItem },
  emits: ["my-choice"],
  props: {
    fruit: Object,
  },
  data() {
    return {
      isActive: false, //если кликнул по фрукту
      lable: "",
    };
  },

  name: "TheAccordion",
};
</script>

<style scoped>
.main__fruit {
  font-size: 25px;
}
.main__fruit::before {
  content: "↓ ";
  transition: all 0.2s linear;
}
.main__fruit:hover::before {
  content: "↓ ";
  color: red;
}
.main__container {
  margin-top: 50px;
  margin-left: 50px;
}
.main__country {
  margin: 20px 15px;
  font-size: 20px;
}
.main__country::before {
  content: "↓ ";
  transition: all 0.2s linear;
}
.main__country:hover::before {
  content: "↓ ";
  color: red;
}
</style>
