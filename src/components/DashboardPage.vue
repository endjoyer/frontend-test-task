<template>
  <div class="dashboard-page">
    <header>
      <span
        >Привет, <span class="username">{{ username }}</span>
      </span>
      <button class="logout-btn" @click="logout">Выйти</button>
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
  padding: 0 24px;

  header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
    padding: 24px 0;

    .username {
      font-weight: 700;
    }

    .logout-btn {
      background: none;
      border: none;
      cursor: pointer;
      font-size: 12px;

      &:hover {
        opacity: 0.8;
      }
    }
  }
}
</style>
