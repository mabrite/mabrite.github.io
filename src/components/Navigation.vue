<template> 
  <nav class="navigation" role="navigation" aria-label="Main Navigation">
    <div class="container">
      <router-link to="/" class="logo" aria-label="MABE Home">
        Welcome To My Portfolio
      </router-link>

      <button
        class="hamburger"
        @click="isMenuOpen = !isMenuOpen"
        :aria-expanded="isMenuOpen.toString()"
        aria-label="Toggle navigation menu"
      >
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>

      <div :class="['nav-links', { open: isMenuOpen }]">
        <router-link to="/" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Home</router-link>
        <router-link to="/skills" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Skills</router-link>
        <router-link to="/contact" exact-active-class="active-tab" class="tab-card" @click="isMenuOpen = false">Contact</router-link>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navigation',
  data() {
    return {
      isMenuOpen: false,
    };
  },
}
</script>

<style scoped>
/* Base Navbar Styles */
.navigation {
  position: sticky;
  top: 0;
  z-index: 110;
  width: 100%;
  padding: 1.5rem 0;
  backdrop-filter: blur(15px);
  background-color: rgba(255, 192, 203, 0.35);
  border-radius: 30px;
  box-shadow: 0 8px 24px rgba(255, 105, 180, 0.2);
  border: #4a0033 solid 2px;
  margin-top: 10px;
  animation: fadeInDown 0.6s ease forwards;
}

/* Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Logo */
.logo {
  font-family: 'Poppins', sans-serif;
  font-weight: 900;
  font-size: 1.8rem;
  color: #d81e5b;
  text-decoration: none;
  letter-spacing: 0.12em;
  transition: color 0.3s ease;
}
.logo:hover {
  color: #ff4d94;
}

/* Nav Links */
.nav-links {
  display: flex;
  gap: 1rem;
}
.tab-card {
  display: inline-block;
  padding: 0.6rem 1.4rem;
  background: rgba(255, 182, 193, 0.75);
  border-radius: 15px;
  font-weight: 600;
  color: #4a0033;
  text-decoration: none;
  box-shadow: 0 3px 6px rgba(255, 105, 180, 0.35);
  transition: all 0.3s ease;
}
.tab-card:hover {
  background-color: #ff6699;
  color: white;
  transform: translateY(-4px) scale(1.05);
  box-shadow: 0 8px 16px rgba(255, 105, 180, 0.5);
}
.active-tab {
  background-color: #d81e5b;
  color: white;
  box-shadow: 0 8px 20px rgba(216, 30, 91, 0.6);
  transform: translateY(-4px) scale(1.1);
  pointer-events: none;
  font-weight: 700;
}

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}
.bar {
  width: 25px;
  height: 3px;
  background-color: #4a0033;
  border-radius: 2px;
  transition: 0.3s ease;
}

/* Tablet Responsiveness */
@media (max-width: 1024px) {
  .container {
    padding: 0 1.2rem;
  }

  .logo {
    font-size: 1.6rem;
  }
}

/* Mobile Responsiveness */
@media (max-width: 768px) {
  .nav-links {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    width: 100%;
    flex-direction: column;
    background: rgba(255, 192, 203, 0.98);
    border: 2px solid #d81e5b;
    border-radius: 15px;
    padding: 1.0rem 1.2rem;
    gap: 1rem;
    margin-top: 1rem;
    display: none;
    animation: slideDown 0.3s ease-in-out;
    z-index: 99;
  }

  .nav-links.open {
    display: flex;
  }

  .tab-card {
    padding: 0.8rem 1.2rem;
    width: 100%;
    font-size: 1rem;
    text-align: left;
  }

  .hamburger {
    display: flex;
    z-index: 100;
  }
}

/* Animations */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10%);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
