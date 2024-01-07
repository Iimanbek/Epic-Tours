<template>
  <div>
    <nav :class="{ 'scrolled-down': isScrolledDown, 'scrolled-up': isScrolledUp }">
      <div class="navbar-container">
        <div class="logo">
          <img src="../../assets/media/logo.jpg"/>
        </div>
        <div class="links">
          <a href="#">Home</a>
          <a href="#">About Us</a>
          <div class="dropdown">
            <a href="#" class="with-tooltip" data-tooltip="Explore our packages">Our Packages</a>
            <div class="dropdown-content">
              <a href="#">Package 1</a>
              <a href="#">Package 2</a>
              <a href="#">Package 3</a>
            </div>
          </div>
          <a href="#">Contacts</a>
        </div>
        <div  class="burger">
          <div class="Burger_wrapper" >
            <div class="menu-wrapper" @click.prevent="openMenu = !openMenu" :class="{ active: openMenu }">
              <div class="menu-bar one"></div>
              <div class="menu-bar two"></div>
            </div>
            <div v-show="openMenu" class="rout_list">
              <nav class="menu">
                <a @click="openMenu = !openMenu" href="/#COURSE" style="animation-delay: 0.1s">Курсы</a>
                <a @click="openMenu = !openMenu" href="/#COMMENTS" style="animation-delay: 0.2s">Отзывы</a>
                <router-link @click="openMenu = !openMenu" to="/teachers" style="animation-delay: 0.3s">Преподаватели</router-link>
                <a @click="openMenu = !openMenu" href="" style="animation-delay: 0.4s">Партнеры</a>
              </nav>
            </div>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>
<script>
export default {
  data() {
    return {
      openMenu: false,
      isScrolledDown: false,
      isScrolledUp: false,
      lastScrollTop: 0,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {

    handleScroll() {
      const scrollTop = window.scrollY;

      // Check if scrolling down
      this.isScrolledDown = scrollTop > this.lastScrollTop && scrollTop > 100;

      // Check if scrolling up
      this.isScrolledUp = scrollTop < this.lastScrollTop && scrollTop > 100;

      this.lastScrollTop = scrollTop;
    },
  },
};
</script>

<style scoped>
.burger{
  display: none;
}
@media screen and (max-width: 800px) {
  .burger{
    display: block;
  }
  .links{
    display: none !important;
  }
}
.menu{
//z-index: 30;
  display: flex;
  flex-direction: column;
  justify-content:center ;
  align-items: center;
  position: absolute;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100%;
  overflow-y: hidden;
  color: white;
  animation-name: appear;
  animation-iteration-count: 1;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;

}
@keyframes appear {
  from{
    background: rgba(0, 0, 0, 0.1);
  }
  to{
    background: rgba(0, 0, 0, 0.5);
  }
}
a{
  display: inline-block;
  margin: 30px 0;
}


.menu-wrapper {
  z-index: 30;
  width: 40px;
  height: auto;
  cursor: pointer;
  position: relative;
}

.menu-bar {
  position: absolute;
  width: 100%;
  height: 4px;
  background: rgb(98 181 229);
  left: 0%;
}



.one {
  top: 0px;
  animation-delay: 0.1s;
  transition: all 0.3s;
}

.two {
  top: 8px;
  transition: all 0.3s;
}


@keyframes slideOut {
  0% {
    width: 100%;
    left: 0%;
    right: auto;
  }

  50% {
    width: 0%;
    left: 0%;
    right: auto;
  }
  51% {
    width: 0%;
    right: 0%;
    left: auto;
  }

  100% {
    width: 100%;
    right: 0%;
    left: auto;
  }
}

.menu-wrapper:hover .menu-bar.active {
  animation:none;
}
.active .one{
  top: 50%;
  left: 0%;
  transform: rotate(45deg);
}
.active .two{
  top: 50%;
  left: 0%;
  transform: rotate(-45deg);
}

.menu-open .bar:nth-child(1) {
  transform: rotate(-45deg) translate(-5px, 6px);
}

.menu-open .bar:nth-child(2) {
  opacity: 0;
}

.menu-open .bar:nth-child(3) {
  transform: rotate(45deg) translate(-5px, -6px);
}




.dropdown {
  position: relative;
}

.dropdown-content {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  padding: 10px;
  z-index: 1;
  min-width: 120px;

}

.dropdown:hover .dropdown-content {
  display: block;
}

.dropdown     .dropdown-content a {
  display: block;
  padding: 5px;
  text-decoration: none;
  color: #333;
  transition: background-color 0.3s ease;
}

.dropdown-content a:hover {
  background-color: #f2f2f2;

}


/* Navbar styles */
nav {
  background-color: rgb(17 17 31);
  transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 10;
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  width: 300px;
  color: #333;
}
.logo img {

  max-height: 50px; /* Set the maximum height for the logo */
}
.links {
  display: flex;
  gap: 20px;
}

.links a {
  text-decoration: none;
  color: rgb(98 181 229);
  font-weight: 600;
  transition: color 0.3s ease;
  font-size: 20px;
}

.links a:hover {
  color: #007bff;
}

/* Scrolled down state */
.scrolled-down {
  background-color: rgb(17 17 31);  transform: translateY(-100%);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Scrolled up state */
.scrolled-up {
  background-color:rgb(17 17 31);;
  transform: translateY(0);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

</style>

