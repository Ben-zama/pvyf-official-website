<template>
  <div class="heroSection">
    <div class="textSection">
      <div class="intro">
        <div class="badge">
          <p>Over <span>500+</span> youths impacted</p>
        </div>
        <div class="heading heading-1">
          <h2>
            Empowering <span>Youths</span>, Transforming
            <span>Communities</span>, Sustaining <span>Livelihoods</span>
          </h2>
        </div>
      </div>

      <div class="info">
        <p>
          The Princess Vanessa Yemilo Foundation (PVYF) is a youth-focused,
          community-driven non-governmental organisation committed to raising a
          generation of purpose-driven, skilled, socially responsible, and
          environmentally conscious young people equipped to create meaningful
          and sustainable change within their communities.
        </p>
      </div>

      <div class="ctas">
        <CtaButton name="Our Impact" />
        <CtaButton name="Join Us" />
      </div>
    </div>

    <div class="imageSection" ref="imageSectionRef">
      <div
        class="image"
        v-for="(img, index) in heroImages"
        :key="img.id"
        :class="{ 'm-hide': img.mHide }"
        :style="{
          '--m-top': `${img.mTop}px`,
          '--d-top': `${img.dTop}px`,
        }"
      >
        <img :src="img.src" alt="" />
        <div
          class="overlay"
          :class="{ 'm-overlay': img.mOverlay, 'd-overlay': img.dOverlay }"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";

const heroImages = [
  {
    id: 1,
    src: "/images/hero/image1.jpg",
    mTop: 0,
    dTop: -25,
    mHide: false,
    mOverlay: false,
    dOverlay: false,
  },
  {
    id: 2,
    src: "/images/hero/image2.jpg",
    mTop: 25,
    dTop: 50,
    mHide: false,
    mOverlay: false,
    dOverlay: false,
  },
  {
    id: 3,
    src: "/images/hero/image3.jpg",
    mTop: 0,
    dTop: 100,
    mHide: false,
    mOverlay: false,
    dOverlay: false,
  },
  {
    id: 4,
    src: "/images/hero/image4.jpg",
    mTop: -25,
    dTop: 50,
    mHide: false,
    mOverlay: true,
    dOverlay: false,
  },
  {
    id: 5,
    src: "/images/hero/image5.jpg",
    mTop: 0,
    dTop: -25,
    mHide: false,
    mOverlay: true,
    dOverlay: false,
  },
  {
    id: 6,
    src: "/images/hero/image6.jpg",
    mTop: -25,
    dTop: -125,
    mHide: false,
    mOverlay: true,
    dOverlay: true,
  },
  {
    id: 7,
    src: "/images/hero/image7.jpg",
    mTop: 0,
    dTop: -50,
    mHide: true,
    mOverlay: false,
    dOverlay: true,
  },
  {
    id: 8,
    src: "/images/hero/image8.jpg",
    mTop: 0,
    dTop: 0,
    mHide: true,
    mOverlay: false,
    dOverlay: true,
  },
  {
    id: 9,
    src: "/images/hero/image9.jpg",
    mTop: 0,
    dTop: -50,
    mHide: true,
    mOverlay: false,
    dOverlay: true,
  },
  {
    id: 10,
    src: "/images/hero/image10.jpg",
    mTop: 0,
    dTop: -125,
    mHide: true,
    mOverlay: false,
    dOverlay: true,
  },
];

const imageSectionRef = ref(null);

onMounted(() => {
  const images = imageSectionRef.value.querySelectorAll(".image");

  gsap.fromTo(
    images,
    {
      y: 100,
      opacity: 0,
      scale: 0.95,
    },
    {
      y: 0,
      opacity: 1,
      scale: 1,
      duration: 1.2,
      stagger: {
        each: 0.1,
        from: "center",
      },
      ease: "power3.out",
      delay: 0.1,
    }
  );
});
</script>

<style lang="scss">
.heroSection {
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 25px;
  overflow: hidden;
  height: max-content;

  .textSection {
    width: 100%;
    margin-top: 25px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 25px;
    text-align: center;

    @include respond-to("md") {
      margin-top: 25px;
      .intro {
        max-width: 75%;
      }
      .info {
        max-width: 75%;
      }
    }

    @include respond-to("xl") {
      .intro {
        max-width: 60%;
      }
      .info {
        max-width: 60%;
      }
    }

    .intro {
      .badge {
        margin: 10px auto;
        padding: 4px 8px;
        width: max-content;
        font-size: 12px;
        border: 1px solid rgba(0, 0, 0, 0.3);
        border-radius: 50px;
        span {
          color: $brand-color-1;
          font-weight: bold;
        }
      }

      .heading {
        h2 {
          font-size: 30px;
        }
        @include respond-to("md") {
          h2 {
            font-size: 42px;
          }
        }
      }
    }
    .info {
      p {
        font-size: 14px;
      }
      @include respond-to("md") {
        p {
          font-size: 16px;
        }
      }
    }
    .ctas {
      display: flex;
      justify-content: center;
      gap: 15px;
    }
  }

  .imageSection {
    position: relative;
    left: -25%;
    width: 150%;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 5px;

    .image {
      position: relative;
      height: 150px;
      width: 100%;
      border-radius: 8px;
      overflow: hidden;
      margin-top: var(--m-top);

      &.m-hide {
        display: none;
      }

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: top;
      }
      .overlay {
        display: none;
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 75px;
        background: linear-gradient(transparent, $background-color 95%);

        &.m-overlay {
          display: block;
        }
      }
    }

    @include respond-to("md") {
      margin-top: -25px;
      width: 125%;
      left: -12.5%;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
      .image {
        height: 200px;
        border-radius: 16px;
        margin-top: var(--d-top);

        &.m-hide {
          display: block; /* Show all on md */
        }

        .overlay {
          display: none; /* Reset */
          &.m-overlay {
            display: none;
          }
          &.d-overlay {
            display: block;
          }
        }
      }
    }

    @include respond-to("xl") {
      margin-top: -50px;
      padding: 0 75px;
      width: 100%;
      left: 0%;
      gap: 15px;
      .image {
        height: 250px;
      }
    }
  }
}
</style>
