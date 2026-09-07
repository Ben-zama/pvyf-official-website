<template>
  <div class="aboutSection">
    <div class="topSection">
      <div class="image">
        <img src="/images/wio.jpg" alt="" />
      </div>

      <div class="text">
        <div class="intro">
          <i class="bi-asterisk"></i>
          <p>Who We Are</p>
        </div>

        <h2>
          Empowering Youths, Transforming Communities, Sustaining Livelihoods
        </h2>

        <p>
          The Princess Vanessa Yemilo Foundation (PVYF) is a youth-focused,
          community-driven non-governmental organisation committed to raising a
          generation of purpose-driven, skilled, socially responsible, and
          environmentally conscious young people equipped to create meaningful
          and sustainable change within their communities.
        </p>

        <ctaButton name="Know Us More" />

        <div class="container">
          <div v-for="item in points" :key="item" class="box">
            <div class="circle">
              <i :class="item.icon"></i>
            </div>
            <h4>{{ item.title }}</h4>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>

    <div class="partners">
      <p>Our Partners over the years</p>
      <div class="marquee-container">
        <ClientOnly>
          <Vue3Marquee :duration="30" :pauseOnHover="true" :clone="true">
            <div v-for="item in partners" :key="item.name" class="image">
              <img :src="item.image" :alt="item.name" />
              <div class="tooltip">{{ item.name }}</div>
            </div>
          </Vue3Marquee>
        </ClientOnly>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Vue3Marquee } from 'vue3-marquee'

const points = [
  {
    icon: "bi-graph-up-arrow",
    title: "Youth Development",
    description:
      "Equipping young people with the knowledge and competencies to become responsible leaders.",
  },
  {
    icon: "bi-brightness-high",
    title: "Environmental Sustainability",
    description:
      "Promoting environmental responsibility through climate education and youth-led solutions.",
  },
  {
    icon: "bi-megaphone",
    title: "SDG Advocacy",
    description:
      "Integrating global development priorities to promote SDG awareness and positive social change.",
  },
  {
    icon: "bi-people",
    title: "Community Empowerment",
    description:
      "Empowering communities through collective action to drive sustainable change.",
  },
];

const partners = [
  { name: "Nigerian Red Cross", image: "/images/partners/nrc.webp" },
  { name: "Kaduna State Environmental Protectiom Authority", image: "/images/partners/kepa.png" },
  { name: "National Youth Council of Nigeria", image: "/images/partners/NYCN.png" },
  { name: "Milton College of Arts & Science", image: "/images/partners/milton.png" },
  { name: "Kaduna State University", image: "/images/partners/kasu.png" },
  { name: "Seven-Up Bottling Company", image: "/images/partners/sbc.png" },
  { name: "ChristHelp Studios", image: "/images/partners/chs.png" },
];
</script>

<style lang="scss">
.aboutSection {
  margin-top: 50px;
  padding: 15px;

  @include respond-to("md") {
    margin-top: 50px;
    padding: 25px;
  }

  @include respond-to("xl") {
    margin-top: 75px;
  }

  .topSection {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 25px;

    @include respond-to("xl") {
      gap: 50px;
    }

    .image {
      width: 500px;
      height: 500px;
      display: none;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: top;
        border-radius: 16px;
      }

      @include respond-to("md") {
        display: block;
      }

      @include respond-to("xl") {
        width: 400px;
        height: 600px;
      }
    }

    .text {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: start;
      justify-content: center;
      gap: 15px;

      @include respond-to("md") {
        width: 100%;
      }

      @include respond-to("xl") {
        width: 50%;
      }

      .intro {
        display: flex;
        align-items: baseline;
        gap: 10px;
        i {
          color: $brand-color-1;
        }
        p {
          font-family: $alternate-font;
        }
      }
      h2 {
        font-weight: 100;
        font-size: 24px;
      }
      .container {
        width: 100%;
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        grid-auto-rows: max-content;
        gap: 15px;

        .box {
          padding: 15px;
          width: 100%;
          display: flex;
          flex-direction: column;
          gap: 10px;
          background: $secondary-color;
          border-radius: 8px;
          .circle {
            width: 36px;
            height: 36px;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
            background: $brand-color-1;
            color: $background-color;
            i {
              font-size: 15px;
              height: 15px;
            }
          }
          h4 {
            font-family: $alternate-font;
            font-weight: bold;
            font-size: 14px;
          }
          p {
            font-size: 12px;
          }
        }
      }
    }
  }

  .partners {
    margin-top: 50px;
    display: flex;
    flex-direction: column;
    align-items: center;
    p {
      width: 75%;
      text-align: center;
      font-family: $alternate-font;
      font-size: 24px;
      color: $brand-color-1;
      font-weight: bold;
    }
    .marquee-container {
      width: 100%;
      margin-top: 25px;
      overflow: hidden;
      mask-image: linear-gradient(to right, transparent, black 10%, black 90%, transparent);
      -webkit-mask-image: linear-gradient(to right, transparent, black 10%, black 90%, transparent);
      .image {
        position: relative;
        margin: 0 40px;
        padding-top: 50px;
        padding-bottom: 10px;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        img {
          height: 80px;
          width: auto;
          object-fit: contain;
        }
        .tooltip {
          position: absolute;
          bottom: 95px;
          left: 50%;
          transform: translateX(-50%) translateY(10px);
          background-color: $brand-color-1;
          color: $background-color;
          padding: 6px 12px;
          border-radius: 4px;
          font-family: $alternate-font;
          font-size: 14px;
          white-space: nowrap;
          opacity: 0;
          visibility: hidden;
          transition: all 0.3s ease;
          pointer-events: none;
          z-index: 10;

          &::after {
            content: '';
            position: absolute;
            top: 100%;
            left: 50%;
            transform: translateX(-50%);
            border-width: 6px;
            border-style: solid;
            border-color: $brand-color-1 transparent transparent transparent;
          }
        }

        &:hover .tooltip {
          opacity: 1;
          visibility: visible;
          transform: translateX(-50%) translateY(0);
        }
      }

      @include respond-to("md") {
        .image {
          margin: 0 50px;
          img {
            height: 100px;
          }
          .tooltip {
            bottom: 115px;
          }
        }
      }
    }
  }
}
</style>