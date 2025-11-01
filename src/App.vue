<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import "./assets/main.css";
</script>

<template>
  <header>
    <nav>
      <div class="nav-logo">
        <a href="#"><h2>Mancingku</h2></a>
      </div>

      <ul class="nav-links">
        <li class="link"><a href="#">BERANDA</a></li>
        <li class="link"><a href="#">TENTANG</a></li>
        <li class="link"><a href="#">SPOT</a></li>
        <li class="link dropdown">
          <a href="#">PERLENGKAPAN <i class="ri-arrow-down-s-line"></i></a>
          <ul class="dropdown-menu">
            <li><a href="#">Umpan</a></li>
            <li><a href="#">Alat Pancing</a></li>
          </ul>
        </li>
      </ul>

      <div class="button">
        <button class="btn-signIN">Masuk</button>
        <button class="btn-signUP">Daftar</button>
      </div>
    </nav>
  </header>

  <main class="container">
    <div class="image-slider">
      <div class="slide active">
        <img src="@/assets/Pemancingan1.jpg" alt="Iklan 1">
      </div>
      <div class="slide">
        <img src="@/assets/Pemancingan2.jpg" alt="Iklan 2">
      </div>
      <div class="slide">
        <img src="@/assets/Pemancingan3.jpg" alt="Iklan 3">
      </div>

      <!-- Navigasi slider -->
      <button class="prev">&#10094;</button>
      <button class="next">&#10095;</button>

      <!-- Dots indikator -->
      <div class="dots">
        <span class="dot active"></span>
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
    </div>

    <div class="content">
      <h1>“Booking Tempat Pemancingan di Sekitar Anda”</h1>
      <p>Temukan pemancingan terdekat, lihat fasilitas dan harga, lalu pesan tempat dengan mudah</p>
      <button class="btn">Lihat</button>
    </div>
  </main>
</template>

<script>
export default {
  name: "HomePage",
  data() {
    return {
      activeSlide: 0,
      slides: [
        { src: "@/assets/Pemancingan1.jpg", alt: "Iklan 1" },
        { src: "@/assets/Pemancingan2.jpg", alt: "Iklan 2" },
        { src: "@/assets/Pemancingan3.jpg", alt: "Iklan 3" },
      ],
    };
  },
  methods: {
    nextSlide() {
      this.activeSlide = (this.activeSlide + 1) % this.slides.length;
    },
    prevSlide() {
      this.activeSlide = (this.activeSlide - 1 + this.slides.length) % this.slides.length;
    },
    goToSlide(index) {
      this.activeSlide = index;
    },
  },
};
</script>

<!-- Global style -->
<style>
html, #app {
  height: 100%;
  margin: 0;
}

body {
  font-family: 'Poppins', sans-serif;
  background-image: url("@/assets/Bg.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
</style>

<!-- Scoped style untuk komponen -->
<style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/remixicon/3.5.0/remixicon.min.css");

/* Reset dasar */
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

img {
  width: 100%;
  display: block;
}

/* Navbar */
nav {
  background-color: #1B3C53;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  gap: 2rem;
}

.nav-logo h2 {
  color: aliceblue;
}

.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 3rem;
}

.link a {
  color: #fff;
  position: relative;
  padding-bottom: 0.75rem;
  text-decoration: none;
}

.link a:hover {
  color: #DA9723;
}

.link a::after {
  content: "";
  position: absolute;
  height: 2px;
  width: 0;
  bottom: 0;
  left: 0;
  background-color: #1d4ed8;
  transition: all 0.3s ease;
}

.link a:hover::after {
  width: 70%;
}

/* Dropdown */
.dropdown {
  position: relative;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: #1B3C53;
  list-style: none;
  padding: 0.5rem 0;
  min-width: 180px;
  border-radius: 5px;
  display: none;
  flex-direction: column;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
  z-index: 10;
}

.dropdown-menu li a {
  display: block;
  padding: 0.5rem 1rem;
  color: #fff;
}

.dropdown-menu li a:hover {
  background-color: #1e40af;
}

.dropdown:hover .dropdown-menu {
  display: flex;
}

/* Tombol */
.btn-signIN, .btn {
  padding: 1rem 2rem;
  font-size: 1rem;
  color: #fff;
  background-color: #DA9723;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn:hover {
  background-color: #1e40af;
}

.btn-signUP {
  padding: 1rem 2rem;
  font-size: 1rem;
  color: #fff;
  border-radius: 5px;
  background-color: #1B3C53;
  cursor: pointer;
}

/* Container dan Main */
.container {
  max-width: 1200px;
  margin: auto;
  padding: 5rem 2rem;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
  gap: 5rem;
}

/* Content */
main .content h4 {
  margin-bottom: 1rem;
  color: #ccc;
  font-size: 1rem;
  font-weight: 600;
}

main .content h1 {
  color: #fff;
  margin-bottom: 1rem;
  font-size: 3rem;
  font-weight: 700;
  line-height: 4rem;
}

main .content p {
  margin-bottom: 2rem;
  color: #ccc;
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
}

/* Slider navigasi */
.image-slider .prev,
.image-slider .next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0,0,0,0.5);
  color: white;
  border: none;
  padding: 12px 18px;
  font-size: 24px;
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s ease;
}

.image-slider .prev:hover,
.image-slider .next:hover {
  background-color: rgba(0,0,0,0.8);
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
  background: rgba(255,255,255,0.6);
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s ease;
}

.dot.active {
  background: #1d4ed8;
}
</style>
