<template>
  <div class="aboutSection">
    <div class="topSection">
      <div class="image">
        <img src="/images/about-image.jpg" alt="" />
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
      <div class="pictureGrid">
        <div v-for="item in partners" :key="item" class="image">
          <img :src="item" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
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
  "/images/partners/nrc.webp",
  "/images/partners/kepa.png",
  "/images/partners/NYCN.png",
  "/images/partners/milton.png",
  "/images/partners/kasu.png",
  "/images/partners/sbc.png",
  "/images/partners/chs.png",
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
        height: 400px;
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
          font-size: 18px;
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
    }
    .pictureGrid {
      width: 100%;
      margin-top: 25px;
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-auto-rows: 80px;
      justify-items: center;
      row-gap: 25px;
      .image {
        grid-column: span 2;
        width: 100%;
        height: 100%;
        img {
          width: 100%;
          height: 100%;
          object-fit: contain;
        }
      }
      :last-child {
        grid-column: span 4;
        padding: 0 7.5%;
      }

      @include respond-to("md") {
        grid-template-columns: repeat(8, 1fr);
        padding: 0 5%;
        :nth-child(6) {
          order: 1;
        }
      }

      @include respond-to("xl") {
        padding: 0 10%;
      }
    }
  }
}
</style>