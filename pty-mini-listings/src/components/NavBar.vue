<template>
  <nav class="navbar">
    <div class="nav-content">

      <!-- Logo -->
      <div class="logo">
        <span>Homes<span class="accent">&</span>Beyond</span>
      </div>

      <!-- Desktop Links -->
      <ul class="nav-links" :class="{ open: menuOpen }">
        <li><a href="#">Home</a></li>
        <li><a href="#">Listings</a></li>
        <li><a href="#">Agents</a></li>
        <li><a href="#">Contact</a></li>

        <li class="fav-mobile">
          <button class="fav-btn">
            ★ <span class="count">{{ favourites }}</span>
          </button>
        </li>
      </ul>

      <!-- Right Section -->
      <div class="right">

        <!-- Favourites Count (desktop) -->
        <button class="fav-btn desktop-only">
          ★ <span class="count">{{ favourites }}</span>
        </button>

        <!-- Hamburger -->
        <button class="hamburger" @click="menuOpen = !menuOpen">
          <div :class="{ active: menuOpen }"></div>
          <div :class="{ active: menuOpen }"></div>
          <div :class="{ active: menuOpen }"></div>
        </button>
      </div>

    </div>
  </nav>
</template>

<script>
export default {
  props: {
    favourites: {
      type: Number,
      default: 0
    }
  },

  data() {
    return {
      menuOpen: false
    };
  }
};
</script>

<style scoped>
/* --- Base Navbar Styling --- */
.navbar {
  width: 100%;
  background: #fff;
  padding: 14px 22px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.08);
  position: sticky;
  top: 0;
  z-index: 50;
}

.nav-content {
  max-width: 1200px;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* --- Logo --- */
.logo {
  font-size: 1.4rem;
  font-weight: 700;
  letter-spacing: 0.5px;
}

.accent {
  color: #1d70b8;
}

/* --- Navigation Links --- */
.nav-links {
  display: flex;
  gap: 24px;
  list-style: none;
}

.nav-links a {
  text-decoration: none;
  color: #333;
  font-weight: 500;
  transition: 0.2s ease;
}

.nav-links a:hover {
  color: #1d70b8;
}

/* --- Favourites Button --- */
.fav-btn {
  background: #1d70b8;
  color: white;
  padding: 8px 12px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  display: flex;
  gap: 6px;
  align-items: center;
}

.fav-btn .count {
  font-weight: 700;
}

/* --- Hamburger --- */
.hamburger {
  width: 30px;
  height: 20px;
  display: none;
  flex-direction: column;
  justify-content: space-between;
  border: none;
  background: none;
  cursor: pointer;
}

.hamburger div {
  width: 100%;
  height: 3px;
  background: #333;
  border-radius: 4px;
  transition: 0.3s;
}

/* When active */
.hamburger div.active:nth-child(1) {
  transform: translateY(8px) rotate(45deg);
}
.hamburger div.active:nth-child(2) {
  opacity: 0;
}
.hamburger div.active:nth-child(3) {
  transform: translateY(-8px) rotate(-45deg);
}

/* --- Mobile Styling --- */
@media(max-width: 850px) {
  .nav-links {
    position: absolute;
    top: 70px;
    right: 20px;
    background: white;
    padding: 20px;
    flex-direction: column;
    gap: 16px;
    border-radius: 12px;
    width: 180px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    display: none;
  }

  .nav-links.open {
    display: flex;
  }

  .desktop-only {
    display: none;
  }

  .hamburger {
    display: flex;
  }

  .fav-mobile {
    display: block;
  }
}

@media(min-width: 851px) {
  .fav-mobile {
    display: none;
  }
}
</style>