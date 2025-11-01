<template>
  <nav class="navbar">
    <div class="nav-logo">
      <RouterLink to="/"><h2>Mancingku</h2></RouterLink>
    </div>

    <!-- Burger button -->
    <div class="burger" @click="toggleMenu">
      <span></span>
      <span></span>
      <span></span>
    </div>

    <!-- Nav Links -->
    <ul class="nav-links" :class="{ open: isOpen }">
      <li class="link"><RouterLink to="/">BERANDA</RouterLink></li>
      <li class="link"><RouterLink to="/tentang">TENTANG</RouterLink></li>
      <li class="link"><RouterLink to="/spot">SPOT</RouterLink></li>

      <!-- Dropdown PERLENGKAPAN -->
      <li class="link dropdown" @click.stop="toggleDropdown">
        <a href="javascript:void(0)">PERLENGKAPAN <i class="ri-arrow-down-s-line"></i></a>
        <ul class="dropdown-menu" :class="{ open: isDropdownOpen }">
          <li><RouterLink to="/umpan">Umpan</RouterLink></li>
          <li><RouterLink to="/peralatan">Alat Pancing</RouterLink></li>
        </ul>
      </li>
    </ul>

    <!-- Desktop Buttons -->
    <div class="button desktop-only">
      <button class="btn-signIN">Masuk</button>
      <button class="btn-signUP">Daftar</button>
    </div>

    <!-- Mobile Buttons -->
    <div class="mobile-buttons" :class="{ open: isOpen }">
      <button class="btn-signIN">Masuk</button>
      <button class="btn-signUP">Daftar</button>
    </div>
  </nav>
</template>

<script setup>
import { ref, watch } from 'vue'

const isOpen = ref(false)
const isDropdownOpen = ref(false)

function toggleMenu() {
  isOpen.value = !isOpen.value
  if (!isOpen.value) {
    isDropdownOpen.value = false // tutup dropdown jika menu ditutup
  }
}

function toggleDropdown() {
  isDropdownOpen.value = !isDropdownOpen.value
}

// Tutup dropdown jika klik di luar
window.addEventListener('click', () => {
  isDropdownOpen.value = false
})
</script>

<style scoped>
@import url("https://cdnjs.cloudflare.com/ajax/libs/remixicon/3.5.0/remixicon.min.css");

.navbar {
  background-color: #1B3C53;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  flex-wrap: wrap;
}

.nav-logo h2 {
  color: aliceblue;
  margin: 0;
}

/* === Links === */
.nav-links {
  list-style: none;
  display: flex;
  align-items: center;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.link a {
  color: #fff;
  text-decoration: none;
  position: relative;
  padding-bottom: 0.5rem;
}

.link a:hover {
  color: #DA9723;
}

/* Hover underline effect */
.link a::after {
  content: "";
  position: absolute;
  height: 2px;
  width: 0;
  bottom: 0;
  left: 0;
  background-color: #DA9723;
  transition: width 0.3s ease;
}
.link a:hover::after {
  width: 70%;
}

/* === Dropdown === */
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

.dropdown-menu.open {
  display: flex;
}

.dropdown-menu li a {
  display: block;
  padding: 0.5rem 1rem;
  color: #fff;
}

.dropdown-menu li a:hover {
  background-color: #1e40af;
}

/* === Buttons === */
.button {
  display: flex;
  gap: 1rem;
}

.btn-signIN, .btn-signUP {
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  color: #fff;
  border-radius: 5px;
  cursor: pointer;
  border: none;
}

.btn-signIN {
  background-color: #DA9723;
}
.btn-signUP {
  background-color: transparent;
  border: 1px solid #DA9723;
}

.desktop-only {
  display: flex;
}

/* === Burger === */
.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
}
.burger span {
  width: 25px;
  height: 3px;
  background-color: #fff;
  border-radius: 2px;
}

/* === Mobile Buttons === */
.mobile-buttons {
  display: none;
  flex-direction: column;
  gap: 0.5rem;
  padding: 0.5rem 0;
}

/* === Responsive === */
@media (max-width: 768px) {
  .burger {
    display: flex;
  }

  .nav-links {
    display: none;
    flex-direction: column;
    width: 100%;
  }

  .nav-links.open {
    display: flex;
  }

  .desktop-only {
    display: none;
  }

  .mobile-buttons {
    display: none;
  }

  .mobile-buttons.open {
    display: flex;
    width: 100%;
  }

  .nav-links .dropdown-menu {
    position: static;
    box-shadow: none;
    background-color: #163347;
    width: 100%;
  }

  .dropdown-menu.open {
    display: flex;
  }

  .link a {
    display: block;
    width: 100%;
  }
}
</style>
