<template>
  <div
    v-for="(item, index) in country.items"
    :key="item"
    @click.stop="click($event, country.title, fruit.title)"
  >
    <div
      @mouseover="mouseOver($event, country.title, fruit.title)"
      @mouseleave="mouseleave($event, country.title, fruit.title)"
      class="main__country-item"
      v-show="index !== 'hide'"
      v-if="country.items.hide"
    >
      {{ item }}
    </div>
    <!--          index != 'hide' - удаляю последнее свойство обьекта из выборки-->
  </div>
</template>

<script>
export default {
  props: {
    country: Object,
    fruit: Object,
  },
  data() {
    return {
      lable: "",
      leave: Boolean,
      mouseClick: false,
    };
  },
  methods: {
    mouseOver(event, country, fruit) {
      event.target.style.backgroundColor = "#b8b8b8";
      this.leave = false;
      this.choice(event, country, fruit);
    },
    mouseleave(event, country, fruit) {
      if (!this.mouseClick) {
        event.target.style.backgroundColor = null;
        this.leave = true;
        this.choice(event, country, fruit);
      }
      event.target.style.backgroundColor = null;
      this.mouseClick = false;
    },
    click(event, country, fruit) {
      this.mouseClick = true;
      this.choice(event, country, fruit);
    },
    choice(event, country, fruit) {
      if (!this.leave) {
        this.lable = fruit + " => " + country + " => " + event.target.innerText;
      } else this.lable = "";
      this.$parent.$emit("my-choice", {
        lable: this.lable,
      });
    },
  },
  name: "TheCountryItem",
};
</script>

<style scoped>
.main__country-item {
  font-size: 15px;
  margin: 15px 25px;
  padding: 5px;
}
</style>
