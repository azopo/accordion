<template>
  <main class="main__wrapper">
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
          <div
              @click.stop='choice($event,  country.title, fruit.title, index)'
              ref="country-item"
              v-for="(item, index) in country.items"
              :key="item"
          >
            <div class="main__country-item" v-show="index !== 'hide'" v-if="country.items.hide">{{
                item
              }}
            </div>
            <!--          index != 'hide' - удаляю последнее свойство обьекта из выборки-->
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  emits: ['my-choice'],
  props: {
    fruit: Object,
  },
  data() {
    return {
      isActive: false, //если кликнул по фрукту
      lable: '',
    };
  },
  methods: {
    choice(event, country, fruit) {
      this.lable = fruit + " => " + country + " => " + event.target.innerText
      this.$emit('my-choice', {
        lable: this.lable
      })
    }
  },
  name: "TheAccordion",
};
</script>

<style scoped>
.main__container {
  display: flex;
  justify-content: center;
}

.main__country {
  margin-left: 50px;
  display: flex;
  flex-direction: column;
}

.main__country-item {
  padding-top: 20px;
  font-style: italic;
}

.main__country-item:hover {
  color: blue;
}

</style>
