<template>
  <div class="projectSection">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Our Flagship Projects</p>
      </div>
      <h2>Programs & Strategic Initiatives</h2>
      <p>
        The Princess Vanessa Yemilo Foundation (PVYF) delivers its mission
        through an integrated ecosystem of youth-centered flagship programs
        designed to move young people from awareness and mindset transformation
        to skills acquisition, leadership development, innovation, advocacy, and
        long-term community impact.
      </p>
    </div>

    <div class="container">
      <div v-for="item in flagship" :key="item" class="card">
        <div class="text">
          <i :class="item.icon"></i>
          <h3>{{ item.title }}</h3>
          <p>{{ item.info }}</p>
          <p class="info2">{{ item.info2 }}</p>
          <ctaButton name="More Info" />
        </div>
        <div class="images">
          <img :src="item.img" alt="" />
        </div>
      </div>
    </div>

    <div class="see-all">
      <ctaButton name="See All Projects" link="all" />
    </div>
  </div>
</template>

<script setup>
const flagship = [
  {
    title: "WakeUp School Outreach",
    info: "The WakeUp School Outreach Program is the Princess Vanessa Yemilo Foundation’s flagship school-based initiative designed to inspire purpose discovery, leadership development, and social responsibility among secondary school students.",
    img: "/images/wio.jpg",
  },
  {
    title: "Work It Out Training",
    info: "The Work It Out Training Program is PVYF’s annual youth empowerment initiative that provides secondary school students and community youths with practical skills, leadership training, entrepreneurship education, and sustainability knowledge during the long vacation period.",
    img: "/images/wio.jpg",
  },
  {
    title: "Work It Out Club Series (WIOCS)",
    info: "The Work It Out Club Series (SDCS) is a three-month weekend vocational and entrepreneurship program designed to equip young people with practical, income-generatingskills that promote self-reliance and sustainable livelihoods.",
    img: "/images/wio.jpg",
  },
];
</script>

<style lang="scss">
.projectSection {
  margin-top: 50px;
  padding: 15px;

  @include respond-to("md") {
    padding: 25px;
  }

  @include respond-to("xl") {
    padding: 25px 100px;
  }

  .heading {
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
      margin: 10px 0;
    }

    @include respond-to("md") {
      max-width: 700px;
      h2 {
        font-size: 30px;
      }
    }
  }

  .container {
    margin-top: 25px;
    display: flex;
    flex-direction: column;
    gap: 25px;
    .card {
      padding: 15px;
      display: flex;
      flex-direction: column;
      gap: 15px;
      border-radius: 16px;
      overflow: hidden;
      .text {
        display: flex;
        flex-direction: column;
        align-items: start;
        gap: 15px;
      }
      .images {
        width: 75%;
        img {
          width: 100%;
          height: 100%;
          border-radius: 8px;
        }
      }
    }
    > :nth-child(1) {
      background: $brand-color-1;
      color: $background-color;
    }
    > :nth-child(2) {
      background: $brand-color-2;
    }
    > :nth-child(3) {
      background: $brand-color-3;
    }

    @include respond-to("md") {
      .card {
        padding: 15px 25px;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;
        .text {
          width: 65%;
          h3 {
            font-size: 24px;
          }
        }
        .images {
          width: 25%;
        }
      }
    }

    @include respond-to("xl") {
      .card {
        padding: 15px 50px;
        .images {
          width: 20%;
        }
      }
    }
  }

  .see-all {
    margin-top: 25px;
    display: flex;
    justify-content: center;
    .button {
      background: $text-color;
      color: $background-color;
      &__icon-wrapper {
        background: $background-color;
        color: $text-color;
      }

      &:hover {
        background: $brand-color-1;
        color: $secondary-color;

        .button__icon-wrapper {
          background: $secondary-color;
          color: $brand-color-1;
        }
      }
    }
  }
}
</style>