<template>
  <div class="dashboard-page">
    <header>
      <span>Привет, {{ username }}</span>
      <button @click="logout">Выйти</button>
    </header>
    <CityDropdown />
    <ImageSlider />
  </div>
</template>

<script>
import { computed } from "vue";
import { useRouter } from "vue-router";
import { useStore } from "vuex";
import CityDropdown from "./CityDropdown.vue";
import ImageSlider from "./ImageSlider.vue";

export default {
  components: {
    CityDropdown,
    ImageSlider,
  },
  setup() {
    const store = useStore();
    const router = useRouter();

    const username = computed(() => store.getters.getUser);

    const logout = () => {
      store.dispatch("logout");
      router.push("/");
    };

    return {
      username,
      logout,
    };
  },
};
</script>

<style scoped lang="scss">
.dashboard-page {
  header {
    display: flex;
    justify-content: space-between;
    padding: 20px;
    background-color: #f5f5f5;
  }
}
</style>
