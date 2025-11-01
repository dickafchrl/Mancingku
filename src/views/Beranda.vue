<template>
  <main class="container">
    <!-- Slider -->
    <div class="image-slider">
      <div 
        v-for="(slide, index) in slides" 
        :key="index" 
        :class="['slide', { active: activeSlide === index }]"
      >
        <img :src="slide.src" :alt="slide.alt" />
      </div>

      <!-- Navigasi slider -->
      <button class="prev" @click="prevSlide">&#10094;</button>
      <button class="next" @click="nextSlide">&#10095;</button>
      <!-- <div style="color:white">DEBUG: HALAMAN BERANDA MUNCUL</div> -->

      <!-- Dots -->
      <div class="dots">
        <span 
          v-for="(slide, index) in slides" 
          :key="index" 
          :class="['dot', { active: activeSlide === index }]" 
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>

    <!-- Konten -->
    <div class="content">
      <h1>“Booking Tempat Pemancingan di Sekitar Anda”</h1>
      <p>Temukan pemancingan terdekat, lihat fasilitas dan harga, lalu pesan tempat dengan mudah</p>
      <button class="btn">Lihat</button>
    </div>
  </main>
</template>

<script setup>
console.log("✅ Beranda berhasil dimuat")
import { ref } from 'vue'

import img1 from '@/assets/Pemancingan1.jpg'
import img2 from '@/assets/Pemancingan2.jpg'
import img3 from '@/assets/Pemancingan3.jpg'

const slides = [
  { src: img1, alt: 'Iklan 1' },
  { src: img2, alt: 'Iklan 2' },
  { src: img3, alt: 'Iklan 3' },
]


const activeSlide = ref(0)

function nextSlide() {
  activeSlide.value = (activeSlide.value + 1) % slides.length
}

function prevSlide() {
  activeSlide.value = (activeSlide.value - 1 + slides.length) % slides.length
}

function goToSlide(index) {
  activeSlide.value = index
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Biar nggak bisa geser kiri kanan di mobile */
html, body {
  overflow-x: hidden;
  width: 100%;
}

.container {
  width: 100%;
  max-width: 1200px;
  margin: auto;
  padding: 5vw 4vw;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
  gap: 4vw;
}

/* Content */
main .content {
  width: 100%;
}

main .content h1 {
  color: #fff;
  margin-bottom: 1rem;
  font-size: clamp(1.8rem, 4vw, 3rem);
  font-weight: 700;
  line-height: 1.3em;
}

main .content p {
  margin-bottom: 2rem;
  color: #ccc;
  font-size: clamp(0.9rem, 2vw, 1.1rem);
}

.btn {
  padding: 0.8rem 1.5rem;
  font-size: clamp(0.9rem, 2vw, 1.1rem);
}

/* Slider */
.image-slider {
  position: relative;
  width: 100%;
  height: 400px;
  overflow: hidden;
}

.image-slider .slide {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.8s ease-in-out;
}

.image-slider .slide.active {
  opacity: 1;
}

.image-slider img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Navigasi slider */
.image-slider .prev,
.image-slider .next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  padding: 12px 18px;
  font-size: 24px;
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s ease;
  z-index: 2;
}

.image-slider .prev:hover,
.image-slider .next:hover {
  background-color: rgba(0, 0, 0, 0.8);
}

.image-slider .prev { left: 10px; }
.image-slider .next { right: 10px; }

/* Slider dots */
.dots {
  position: absolute;
  bottom: 15px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
}

.dot {
  width: 12px;
  height: 12px;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s ease;
}

.dot.active {
  background: #1d4ed8;
}

/* Responsif di mobile */
@media (max-width: 768px) {
  .container {
    grid-template-columns: 1fr;
    text-align: center;
    padding: 4vw 3vw;
    gap: 2rem;
  }

  .image-slider {
    height: 55vw;
  }

  .image-slider .prev,
  .image-slider .next {
    padding: 8px 12px;
    font-size: 20px;
  }

  main .content h1 {
    font-size: 1.8rem;
    line-height: 2.2rem;
  }

  main .content p {
    font-size: 1rem;
  }
}
</style>

