<template>
  <div class="city-dropdown">
    <multiselect
      v-model="selectedCity"
      :options="cities"
      placeholder="Введите город"
    />
    <div class="city-text-container" v-if="selectedCity">
      <h2>{{ selectedCity }}</h2>
      <p>
        Lorem ipsum dolor sit amet consectetur. Elementum donec a accumsan
        egestas et non diam nunc. Semper aenean pharetra sit morbi. Est sed enim
        ut commodo adipiscing curabitur elementum tristique vel. Felis cras nisi
        et blandit. Vitae aliquam interdum aliquam ac senectus sit non erat.
        Euismod eu non id fermentum urna nunc scelerisque cursus vel. Phasellus
        ullamcorper congue ac tortor quam in mauris. Aliquam suspendisse erat
        dictumst libero. Commodo facilisis accumsan mattis pellentesque turpis
        nibh. Amet aliquam volutpat dictum risus nulla rhoncus arcu turpis
        tellus. Cursus feugiat quam arcu leo purus suspendisse cursus risus
        quis. Massa lobortis dolor a cras diam. Mi purus volutpat pulvinar
        accumsan dolor ultricies. Ipsum cursus proin mauris in. Bibendum amet
        ultrices faucibus tellus mauris magna. Eget leo sed aliquam eget tempus
        eget viverra tincidunt sit. Tortor non elit felis cras cras mi eget. Ut
        aliquet nibh eu at. Laoreet tincidunt porttitor tellus tristique.
      </p>
    </div>
    <div class="city-text-container" v-else>
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
  max-width: 660px;
  padding: 20px 0;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;

  /* Используем :deep отдельно для каждого элемента */
  :deep(.multiselect) {
    width: 230px;
    border-radius: 8px;
    font-size: 12px;
    font-weight: 400;
  }

  :deep(.multiselect__select:before) {
    top: 60%;
  }

  :deep(.multiselect__tags .multiselect__single) {
    padding: 0;
    font-size: 12px;
    font-weight: 400;
  }

  :deep(.multiselect__input) {
    padding: 0;
    font-size: 12px;
    font-weight: 400;
  }

  :deep(.multiselect__tags) {
    display: flex;
    align-items: center;
  }

  :deep(.multiselect__option::after) {
    display: none;
  }

  .city-text-container {
    max-width: 100%;
    min-height: 260px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 30px;
    padding: 15px 0;

    h2,
    p {
      margin: 0;
    }

    h2 {
      font-size: 16px;
      font-weight: 700;
    }
  }
}
</style>
