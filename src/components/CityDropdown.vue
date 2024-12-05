<template>
  <div class="city-dropdown">
    <multiselect
      v-model="selectedCity"
      :options="cities"
      placeholder="Введите город"
    />
    <div v-if="selectedCity">
      <h2>{{ selectedCity }}</h2>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Error soluta
        repellat cumque corporis itaque quis. Iusto repellendus, eius optio quam
        dignissimos, laboriosam praesentium quaerat, ipsa similique tenetur sed
        voluptatibus saepe.
      </p>
    </div>
    <div v-else>
      <p>Город не выбран</p>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import Multiselect from "vue-multiselect";

export default {
  components: {
    Multiselect,
  },
  setup() {
    const selectedCity = ref(null);
    const cities = ref([
      "Москва",
      "Санкт-Петербург",
      "Новосибирск",
      "Екатеринбург",
      "Казань",
      "Нижний Новгород",
      "Челябинск",
      "Самара",
      "Омск",
      "Ростов-на-Дону",
    ]);

    return {
      selectedCity,
      cities,
    };
  },
};
</script>

<style scoped lang="scss">
@import "vue-multiselect/dist/vue-multiselect.min.css";

.city-dropdown {
  width: 230px;
  margin: 20px auto;
  .multiselect {
    width: 100%;
    border: 1px solid #d7d7d7;
    border-radius: 8px;
    padding: 8px 16px;
  }
}
</style>
