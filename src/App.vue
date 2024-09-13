<template>
  <div id="app" class="container">

    <h2>Click Counter</h2>
    <button @click="count++">You clicked me {{ count }} times</button>


    <h2>Box Color Changer</h2>
    <div :style="{ backgroundColor: currentColor, width: '100px', height: '100px' }"></div>
    <button @click="changeColor">Change Box Color</button>

    
    <h2>Image Carousel</h2>
    <div class="carousel">
      <button @click="prevImage">Previous</button>
      <img :src="images[currentImage]" alt="Carousel Image" width="300" height="200">
      <button @click="nextImage">Next</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    // Click Counter
    const count = ref(0);

    // Box Color Changer
    const colors = ['red', 'blue', 'green', 'yellow', 'purple'];
    const currentColor = ref(colors[0]);

    const changeColor = () => {
      currentColor.value = colors[Math.floor(Math.random() * colors.length)];
    };

    // Image Carousel
    const images = ref([
      'https://via.placeholder.com/300x200/ff7f7f/333333?text=Image+1',
      'https://via.placeholder.com/300x200/7f7fff/333333?text=Image+2',
      'https://via.placeholder.com/300x200/7fff7f/333333?text=Image+3'
    ]);

    const currentImage = ref(0);

    const nextImage = () => {
      currentImage.value = (currentImage.value + 1) % images.value.length;
    };

    const prevImage = () => {
      currentImage.value = (currentImage.value - 1 + images.value.length) % images.value.length;
    };

    return {
      count,
      currentColor,
      changeColor,
      images,
      currentImage,
      nextImage,
      prevImage
    };
  }
};
</script>




