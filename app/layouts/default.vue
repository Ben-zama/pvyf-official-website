<template>
  <div id="mainLayout">
    <header>
      <NuxtLink class="logo" to="/">
        <img src="/images/full.png" alt="" />
      </NuxtLink>

      <div class="navigation">
        <NuxtLink to="/about">Who we are</NuxtLink>
        <NuxtLink to="/projects">Our Projects</NuxtLink>
        <NuxtLink to="/volunteer">Get Involved</NuxtLink>
        <NuxtLink to="/contact">Contact Us</NuxtLink>
      </div>

      <div class="side">
        <ctaButton name="Work It Out 2026" link="/contact" />
        <div class="hamburger" ref="hamburgerRef" @click="toggleMenu">
          <Hamburger :isOpen="isMenuOpen" />
        </div>
      </div>
    </header>

    <div class="ripples" ref="ripplesRef">
      <div class="ripple ripple-1" ref="ripple1"></div>
      <div class="ripple ripple-2" ref="ripple2"></div>
      <div class="ripple ripple-3" ref="ripple3"></div>
      <div class="ripple ripple-4" ref="ripple4"></div>
    </div>

    <aside class="mobile-menu" ref="mobileMenuRef">
      <MobileMenu @close-menu="closeMenu" />
    </aside>

    <main>
      <NuxtPage />
    </main>

    <footer>
      <div class="logo">
        <img src="/images/full.png" alt="" />
      </div>

      <div class="middle">
        <div class="col">
          <p class="quote">
            Empowering Youths, Transforming Communities, Sustaining Livelihoods
          </p>

          <div class="ctas">
            <ctaButton name="Our Impact" link="/" />
            <ctaButton name="Join Us" link="/" />
          </div>

          <div class="socials">
            <a href="" target="_blank">
              <i class="bi-instagram"></i>
            </a>
            <a href="" target="_blank">
              <i class="bi-twitter-x"></i>
            </a>
            <a href="" target="_blank">
              <i class="bi-linkedin"></i>
            </a>
            <a href="" target="_blank">
              <i class="bi-facebook"></i>
            </a>
          </div>
        </div>

        <div class="link left-link">
          <h4>Quick Links</h4>
          <NuxtLink to="/">Home</NuxtLink>
          <NuxtLink to="/">Who We Are</NuxtLink>
          <NuxtLink to="/">Our Projects</NuxtLink>
          <NuxtLink to="/">Get Involved</NuxtLink>
          <NuxtLink to="/">Contact Us</NuxtLink>
        </div>

        <div class="link right-link">
          <h4>Key Projects</h4>
          <NuxtLink to="/">Work It Out</NuxtLink>
          <NuxtLink to="/">Wake Up</NuxtLink>
          <NuxtLink to="/">Upcycling Recyclable Waste</NuxtLink>
          <NuxtLink to="/">Personal & Skill Development</NuxtLink>
        </div>
      </div>

      <div class="copyright">
        <p>&copy;Copyright <span>2026</span>, PVYF - All Rights Reserved</p>
        <p>
          Powered by
          <a href="https://benzama-dev.vercel.app" target="_blank">Benzama</a>
        </p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";

const isMenuOpen = ref(false);
const hamburgerRef = ref(null);
const mobileMenuRef = ref(null);
const ripplesRef = ref(null);

const ripple1 = ref(null);
const ripple2 = ref(null);
const ripple3 = ref(null);
const ripple4 = ref(null);

let tl;

const getScale = () => {
  const containerWidth = ripplesRef.value
    ? ripplesRef.value.offsetWidth
    : window.innerWidth;
  const diag = Math.sqrt(containerWidth ** 2 + window.innerHeight ** 2);
  return diag / 20; // 40px base size -> 20px radius
};

onMounted(() => {
  tl = gsap.timeline({ paused: true });

  tl.to(ripple1.value, {
    scale: () => getScale(),
    duration: 0.6,
    ease: "power2.inOut",
  })
    .to(
      ripple2.value,
      { scale: () => getScale(), duration: 0.6, ease: "power2.inOut" },
      "-=0.45"
    )
    .to(
      ripple3.value,
      { scale: () => getScale(), duration: 0.6, ease: "power2.inOut" },
      "-=0.45"
    )
    .to(
      ripple4.value,
      { scale: () => getScale(), duration: 0.6, ease: "power2.inOut" },
      "-=0.45"
    )
    .to(mobileMenuRef.value, { autoAlpha: 1, duration: 0.3 }, "-=0.3");
});

const toggleMenu = () => {
  if (isMenuOpen.value) {
    isMenuOpen.value = false;
    tl.reverse();
  } else {
    isMenuOpen.value = true;

    const rect = hamburgerRef.value.getBoundingClientRect();
    const ripplesRect = ripplesRef.value.getBoundingClientRect();
    const centerX = rect.left + rect.width / 2 - ripplesRect.left;
    const centerY = rect.top + rect.height / 2 - ripplesRect.top;

    gsap.set([ripple1.value, ripple2.value, ripple3.value, ripple4.value], {
      left: centerX,
      top: centerY,
      xPercent: -50,
      yPercent: -50,
    });

    tl.invalidate().play();
  }
};

const closeMenu = () => {
  if (isMenuOpen.value) {
    isMenuOpen.value = false;
    tl.reverse();
  }
};
</script>

<style lang="scss">
#mainLayout {
  header {
    padding: 0 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    height: 90px;

    .logo {
      width: 60%;
      height: 100%;
      img {
        width: 100%;
        height: 100%;
        object-fit: contain;
      }
    }

    .navigation {
      display: none;
      align-items: center;
      gap: 25px;
      font-family: $alternate-font;
      a {
        position: relative;
        transition: 0.3s;
        &:before {
          content: "";
          position: absolute;
          bottom: -2px;
          left: 50%;
          transform: translateX(-50%);
          width: 0;
          height: 2px;
          border-radius: 10px;
          background: $brand-color-1;
          transition: 0.3s;
        }
        &:hover {
          color: $brand-color-1;
          &::before {
            width: 100%;
          }
        }
      }
      .router-link-exact-active {
        position: relative;
        color: $brand-color-1;
        transition: 0.3s;
        &:before {
          content: "";
          position: absolute;
          bottom: -2px;
          left: 50%;
          transform: translateX(-50%);
          width: 100%;
          height: 2px;
          border-radius: 10px;
          background: $brand-color-1;
          transition: 0.3s;
        }
      }
    }

    .side {
      display: flex;
      align-items: center;
      gap: 25px;
      .button {
        display: none;
      }
      .hamburger {
        position: relative;
        z-index: 11;
        width: 36px;
        height: 36px;
        display: flex;
        justify-content: center;
        align-items: center;
        background: $secondary-color;
        border-radius: 6px;
        cursor: pointer;
      }
    }

    @include respond-to("md") {
      height: 100px;
      padding: 0 25px;
      .logo {
        width: auto;
        padding: 15px 0;
      }
      .side {
        .button {
          display: flex;
        }
        .hamburger {
          width: 42px;
          height: 42px;
        }
      }
    }

    @include respond-to("xl") {
      padding: 0 50px;
      .navigation {
        display: flex;
      }
    }
  }

  /* Mobile Menu */
  .ripples {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    pointer-events: none;
    z-index: 10;
    overflow: hidden;

    @include respond-to("xl") {
      width: 400px;
      right: 0;
      left: auto;
    }

    .ripple {
      position: absolute;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      transform: translate(-50%, -50%) scale(0);
      will-change: transform;
      &.ripple-1 {
        background: $brand-color-1;
      }
      &.ripple-2 {
        background: $brand-color-2;
      }
      &.ripple-3 {
        background: $brand-color-3;
      }
      &.ripple-4 {
        background: $secondary-color;
      }
    }
  }

  aside.mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    padding: 24px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    background: transparent;
    z-index: 10;
    opacity: 0;
    visibility: hidden;

    @include respond-to("xl") {
      padding: 36px;
      width: 400px;
      right: 0;
      left: auto;
      justify-content: start;
      gap: 50px;
    }
  }

  footer {
    position: relative;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 25px;
    padding: 25px 15px;
    background: $background-color;
    @include respond-to("md") {
      gap: 50px;
      padding: 25px;
    }

    .logo {
      width: 75%;
      height: auto;
      img {
        width: 100%;
        height: 100%;
        object-fit: contain;
      }
      @include respond-to("md") {
        width: 35%;
      }
      @include respond-to("xl") {
        width: 30%;
      }
    }

    .middle {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 25px;

      .col {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 25px;
        grid-column: span 2;

        .quote {
          font-family: $alternate-font;
          font-size: 24px;
          text-align: center;
        }
        .ctas {
          display: flex;
          align-items: center;
          gap: 15px;
        }
        .socials {
          display: flex;
          gap: 15px;
          a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 60px;
            height: 35px;
            border: 1px solid;
            border-radius: 32px;
            transition: 0.3s;
            i {
              font-size: 18px;
              height: 18px;
            }
            &:hover {
              background: $brand-color-1;
              border-color: $brand-color-1;
              transform: scale(1.1);
              i {
                color: $background-color;
              }
            }
          }
        }
      }

      .link {
        width: 100%;
        display: flex;
        flex-direction: column;
        gap: 5px;
        h4 {
          font-size: 18px;
          letter-spacing: 1px;
        }
        a {
          transition: 0.3s;
          &:hover {
            color: $brand-color-1;
          }
        }
        &.left-link {
          align-items: flex-end;
        }
      }

      @include respond-to("md") {
        grid-template-columns: repeat(3, 1fr);
        gap: 75px;
        .col {
          grid-column: span 1;
        }
        .left-link {
          order: -1;
        }
      }

      @include respond-to("xl") {
        grid-template-columns: repeat(4, 1fr);
        .col {
          grid-column: span 2;
          .quote {
            padding: 0 15%;
          }
        }
      }
    }

    .copyright {
      text-align: center;
      a {
        position: relative;
        font-family: $cursive-font;
        font-weight: bold;
        color: $brand-color-1;
        &:before {
          content: "";
          position: absolute;
          left: 0;
          bottom: -1px;
          height: 2px;
          width: 0;
          background: $brand-color-1;
          transition: 0.3s;
        }
        &:hover {
          &:before {
            width: 100%;
          }
        }
      }
    }
  }
}
</style>