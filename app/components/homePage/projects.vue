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
      <projectCard
        v-for="(item, index) in flagship"
        :key="index"
        :item="item"
      />
    </div>

    <div class="see-all">
      <ctaButton name="See All Projects" link="projects" />
    </div>
  </div>
</template>

<script setup>
const flagship = [
  {
    title: "WakeUp School Outreach",
    info: "The WakeUp School Outreach Program is the Princess Vanessa Yemilo Foundation’s flagship school-based initiative designed to inspire purpose discovery, leadership development, and social responsibility among secondary school students.",
    img: "/illustrations/wuso.svg",
  },
  {
    title: "Work It Out Training Program and Exhibition Day",
    info: "The Work It Out Training Program and Exhibition Day is PVYF’s annual youth empowerment initiative that provides secondary school students and community youths with practical skills, leadership training, entrepreneurship education, and sustainability knowledge during the long vacation period.",
    img: "/illustrations/wio.svg",
  },
  {
    title: "Work It Out Club Series (WIOCS)",
    info: "The Work It Out Club Series (WIOCS) is a weekend vocational and entrepreneurship program designed to equip young people with practical, income-generating skills that promote self-reliance and sustainable livelihoods.",
    img: "/illustrations/wiocs.svg",
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
      }
    }
    h2 {
      margin: 10px 0;
    }

    @include respond-to("md") {
      max-width: 700px;
      h2 {
        font-size: 32px;
      }
    }
  }

  .container {
    margin-top: 25px;
    display: flex;
    flex-direction: column;
    gap: 25px;
    color: white;
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
        color: $primary-color;

        .button__icon-wrapper {
          background: $primary-color;
          color: $brand-color-1;
        }
      }
    }
  }
}
</style>