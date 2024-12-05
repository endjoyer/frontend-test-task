<template>
  <div class="image-slider">
    <div class="slider-container">
      <div
        class="slider-track"
        :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
      >
        <div class="slider-slide" v-for="(image, index) in images" :key="index">
          <img :src="image" alt="Slide Image" />
        </div>
      </div>
      <button class="slider-btn prev" @click="prevSlide">‹</button>
      <button class="slider-btn next" @click="nextSlide">›</button>
    </div>
    <div class="slider-indicators">
      <span
        v-for="(image, index) in images"
        :key="index"
        class="indicator"
        :class="{ active: currentSlide === index }"
        @click="goToSlide(index)"
      ></span>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from "vue";

export default {
  setup() {
    const images = ref([
      "https://cdn.tripster.ru/thumbs2/bb93043c-9b18-11ed-b455-fa17e0b83c4a.1220x600.jpeg",
      "https://sutochno.ru/doc/images/galleries/180/luchshie2.jpg",
      "https://cdn.tripster.ru/thumbs2/5558ad9a-8bdf-11ed-9952-e696d080bbb0.1220x600.jpeg",
    ]);
    const currentSlide = ref(0);

    const nextSlide = () => {
      currentSlide.value =
        currentSlide.value === images.value.length - 1
          ? 0
          : currentSlide.value + 1;
    };

    const prevSlide = () => {
      currentSlide.value =
        currentSlide.value === 0
          ? images.value.length - 1
          : currentSlide.value - 1;
    };

    const goToSlide = (index) => {
      currentSlide.value = index;
    };

    onMounted(() => {
      const interval = setInterval(() => {
        nextSlide();
      }, 5000);

      onUnmounted(() => {
        clearInterval(interval);
      });
    });

    return {
      images,
      currentSlide,
      nextSlide,
      prevSlide,
      goToSlide,
    };
  },
};
</script>

<style scoped lang="scss">
.image-slider {
  width: 600px;
  margin: 20px auto;
  position: relative;

  .slider-container {
    overflow: hidden;
    position: relative;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);

    .slider-track {
      display: flex;
      transition: transform 0.5s ease-in-out;
    }

    .slider-slide {
      flex: 0 0 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      img {
        width: 100%;
        height: auto;
        display: block;
      }
    }

    .slider-btn {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background-color: rgba(0, 0, 0, 0.5);
      color: #fff;
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      cursor: pointer;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      transition: background-color 0.3s;
      z-index: 10;

      &:hover {
        background-color: rgba(0, 0, 0, 0.8);
      }

      &.prev {
        left: 10px;
      }

      &.next {
        right: 10px;
      }
    }
  }

  .slider-indicators {
    display: flex;
    justify-content: center;
    margin-top: 10px;

    .indicator {
      width: 10px;
      height: 10px;
      margin: 0 5px;
      border-radius: 50%;
      background-color: #ddd;
      cursor: pointer;
      transition: background-color 0.3s;

      &.active {
        background-color: #007bff;
      }
    }
  }
}
</style>
