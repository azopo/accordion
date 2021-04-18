<template>
  <main class="main__wrapper">
    <div class="main__container">
      <!--      название фрукта и при клике открываю страну-->
      <p class="main__fruit" @click="isActive = !isActive">{{ fruit.title }}</p>
      <!--        показываю если кликнул-->
      <div class="country__container">
        <p
          v-show="isActive"
          class="main__country"
          v-for="country in fruit.country"
          :key="country.title"
          @click="country.items.hide = !country.items.hide"
        >
          <!--        country.items.hide = !country.items.hide - изменяю внутренее свойство обьекта-->
          {{ country.title }}
          <span
            class="main__country-item"
            v-for="(item, index) in country.items"
            @click.stop="active"
            :key="item"
          >
            <span v-show="index !== 'hide'" v-if="country.items.hide">{{
              item
            }}</span>
            <!--          index != 'hide' - удаляю последнее свойство обьекта из выборки-->
          </span>
        </p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  props: {
    fruit: Object,
  },
  data() {
    return {
      isActive: false, //если кликнул по фрукту
    };
  },
  methods: {
    active(event) {
      event.target.classList.add('active')
    },
  },
  name: "TheAccordion",
};
</script>

<style scoped>
.main__container {
  display: flex;
}

.main__country {
  margin-left: 50px;
  display: flex;
  flex-direction: column;
}

.main__country-item {
  display: none;
  padding-top: 20px;
}
.active{
  display: block;
  color: blue;
}
</style>
