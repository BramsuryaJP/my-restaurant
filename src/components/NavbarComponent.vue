<template>
  <header :class="{ 'scrolled-nav': scrolledNav }">
    <nav>
      <a class="logo" to="/">My Restaurant</a>
      <ul v-show="!mobile" class="navigation">
        <li>
          <router-link class="link" :to="{ name: 'Home' }">Home</router-link>
        </li>
        <li>
          <router-link class="link" :to="{ name: 'Gallery' }"
            >Gallery</router-link
          >
        </li>
      </ul>
      <ul v-show="!mobile" class="navigation-right">
        <li>
          <router-link class="link cart" :to="{ name: 'Cart' }"
            >Cart<i class="far fa-shopping-bag"></i
            ><span>(4)</span></router-link
          >
        </li>
      </ul>
      <div class="icon">
        <i
          @click="toggleMobileNav"
          v-show="mobile"
          class="far fa-bars"
          :class="{ 'icon-active': mobileNav }"
        ></i>
      </div>
      <transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav">
          <li>
            <router-link class="link" :to="{ name: 'Home' }">Home</router-link>
          </li>
          <li>
            <router-link class="link" :to="{ name: 'Gallery' }"
              >Gallery</router-link
            >
          </li>
          <li>
            <router-link class="link" :to="{ name: 'Cart' }"
              >Cart<i class="far fa-shopping-bag"></i
              ><span>(4)</span></router-link
            >
          </li>
        </ul>
      </transition>
    </nav>
  </header>
</template>

<script>
export default {
  name: "NavbarComponent",
  data() {
    return {
      scrolledNav: null,
      mobile: null,
      mobileNav: null,
      windowWidth: null,
    };
  },

  created() {
    window.addEventListener("resize", this.checkScreen);
    this.checkScreen();
  },

  mounted() {
    window.addEventListener("scroll", this.updateScroll);
  },

  methods: {
    toggleMobileNav() {
      this.mobileNav = !this.mobileNav;
    },

    updateScroll() {
      const scrollPosition = window.scrollY;
      if (scrollPosition > 50) {
        this.scrolledNav = true;
        return;
      }
      this.scrolledNav = false;
    },

    checkScreen() {
      this.windowWidth = window.innerWidth;
      if (this.windowWidth <= 750) {
        this.mobile = true;
        return;
      }
      this.mobile = false;
      this.mobileNav = false;
      return;
    },
  },
};
</script>

<style lang="scss">
header {
  background-color: #77a4e5;
  z-index: 99;
  width: 100%;
  position: fixed;
  transition: 0.5s ease all;
  color: #fff;

  nav {
    position: relative;
    display: flex;
    flex-direction: row;
    padding: 12px 0;
    transition: 0.5s ease all;
    margin: 0 auto;
    align-items: center;

    @media (min-width: 1280px) {
      max-width: 1280px;
    }

    .logo {
      font-size: 22px;
      font-weight: bold;
      padding: 16px;
      text-transform: uppercase;
      text-decoration: none;
      color: #fff;
      cursor: pointer;
    }

    ul,
    .link {
      font-weight: 500;
      color: #fff;
      text-decoration: none;
      list-style: none;
    }

    li {
      text-transform: uppercase;
      padding: 16px;
      margin-left: 16px;
    }

    .link {
      font-size: 14px;
      transition: 0.5s ease all;
      padding-bottom: 4px;
      border-bottom: 1px solid transparent;
      transition: 0.3s ease all;

      &:active {
        color: #fa9746;
        border-color: #fa9746;
      }
    }

    a.router-link-active {
      color: #fa9746;
      border-color: #fa9746;
    }

    .navigation {
      display: flex;
      flex: 1;
    }

    .navigation-right {
      display: flex;
      justify-content: flex-end;

      i {
        margin-left: 5px;
      }

      span {
        margin-left: 5px;
      }
    }

    .icon {
      display: flex;
      align-items: center;
      position: absolute;
      top: 0;
      right: 24px;
      height: 100%;

      i {
        cursor: pointer;
        font-size: 24px;
        transition: 0.8s ease all;
      }
    }

    .icon-active {
      transform: rotate(180deg);
    }

    .dropdown-nav {
      display: flex;
      flex-direction: column;
      position: fixed;
      width: 100%;
      max-width: 250px;
      height: 100%;
      background-color: #fff;
      top: 0;
      left: 0;

      li {
        margin-left: 0;

        .link {
          color: black;
        }

        i {
          margin-left: 5px;
        }
      }
    }

    .mobile-nav-enter-active,
    .mobile-nav-leave-active {
      transition: 1s ease all;
    }

    .mobile-nav-enter-from,
    .mobile-nav-leave-to {
      transform: translateX(-250px);
    }

    .mobile-nav-enter-to {
      transform: translateX(0);
    }
  }
}

.scrolled-nav {
  nav {
    padding: 8px 0;

    .logo {
      font-size: 20px;
    }
  }
}
</style>