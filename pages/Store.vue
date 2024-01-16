<template>
  <div>
    <div
      id="default-carousel"
      class="relative py-40 w-full"
      data-carousel="slide"
    >
      <!-- Carousel wrapper -->
      <div class="relative h-56 rounded-lg md:h-96">
        <!-- Slide items -->
        <div
          v-for="(item, index) in carouselItems"
          :key="index"
          :class="{
            'duration-700 ease-in-out': currentIndex === index,
            hidden: currentIndex !== index,
          }"
          data-carousel-item
        >
          <img
            :src="item.src"
            class="absolute block w-full -translate-x-1/2 -translate-y-1/2 top-1/2 left-1/2"
            :alt="item.alt"
          />
        </div>
      </div>
      <!-- Slider indicators -->
      <div
        class="absolute z-30 flex -translate-x-1/2 bottom-5 left-1/2 space-x-3 rtl:space-x-reverse"
      >
        <button
          v-for="(item, index) in carouselItems"
          :key="index"
          type="button"
          class="w-3 h-3 rounded-full"
          :aria-current="currentIndex === index"
          :aria-label="`Slide ${index + 1}`"
          :data-carousel-slide-to="index"
          @click="goToSlide(index)"
        ></button>
      </div>
      <!-- Slider controls -->
      <button
        type="button"
        class="absolute top-0 start-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
        data-carousel-prev
        @click="goToPrevSlide"
      >
        <span
          class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none"
        >
          <svg
            class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 6 10"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 1 1 5l4 4"
            />
          </svg>
          <span class="sr-only">Previous</span>
        </span>
      </button>
      <button
        type="button"
        class="absolute top-0 end-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none"
        data-carousel-next
        @click="goToNextSlide"
      >
        <span
          class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none"
        >
          <svg
            class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 6 10"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="m1 9 4-4-4-4"
            />
          </svg>
          <span class="sr-only">Next</span>
        </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      carouselItems: [
        { src: "w.png", alt: "Slide 1" },
        { src: "sto.png", alt: "Slide 2" },
        { src: "card.png", alt: "Slide 3" },
        { src: "reser.png", alt: "Slide 4" },
        { src: "thank.png", alt: "Slide 5" },
      ],
      autoSlideInterval: null,
    };
  },
  methods: {
    goToSlide(index) {
      this.currentIndex = index;
    },
    goToNextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.carouselItems.length;
    },
    goToPrevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.carouselItems.length) %
        this.carouselItems.length;
    },
    startAutoSlide() {
      this.autoSlideInterval = setInterval(() => {
        this.goToNextSlide();
      }, 3000); // Change the time interval (in milliseconds) as needed
    },
    stopAutoSlide() {
      clearInterval(this.autoSlideInterval);
    },
  },
  mounted() {
    this.startAutoSlide(); // Start auto sliding when component is mounted
  },
  beforeDestroy() {
    this.stopAutoSlide(); // Stop auto sliding when component is destroyed
  },
};
</script>
