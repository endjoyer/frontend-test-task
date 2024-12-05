<template>
  <div class="image-slider">
    <vue-slider
      v-model="currentSlide"
      :min="0"
      :max="images.length - 1"
      :interval="3000"
      :autoplay="true"
      :loop="true"
    >
      <template #default="{ value }">
        <img :src="images[value]" alt="Slide Image" />
      </template>
    </vue-slider>
  </div>
</template>

<script>
import { ref } from "vue";
import VueSlider from "@vueform/slider";

export default {
  components: {
    VueSlider,
  },
  setup() {
    const currentSlide = ref(0);
    const images = ref([
      "https://via.placeholder.com/600x300?text=Slide+1",
      "https://via.placeholder.com/600x300?text=Slide+2",
      "https://via.placeholder.com/600x300?text=Slide+3",
    ]);

    return {
      currentSlide,
      images,
    };
  },
};
</script>

<style scoped lang="scss">
.image-slider {
  width: 600px;
  margin: 20px auto;
  img {
    width: 100%;
    border-radius: 8px;
  }
}
</style>
