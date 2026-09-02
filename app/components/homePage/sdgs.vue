<template>
  <div class="sdgSection">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Alignment with the SDGs</p>
      </div>
      <h2>Driving Global Goals Locally</h2>
      <p>
        Integrating the United Nations Sustainable Development Goals into every
        community initiative
      </p>
    </div>

    <div class="container">
      <div
        v-for="sdg in sdgs"
        :key="sdg.no"
        class="sdg-card"
        :style="{ backgroundColor: sdg.bgColor }"
      >
        <div class="card-header">
          <div class="span">
            <span>{{ sdg.no }}</span>
            <div class="name">
              <h3>{{ sdg.name }}</h3>
              <h3>{{ sdg.name2 }}</h3>
            </div>
          </div>
          <div class="icon">
            <img :src="sdg.image" :alt="`SDG ${sdg.no} - ${sdg.name}`" />
          </div>
        </div>
        <div class="card-body">
          <p>{{ sdg.info }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const sdgs = [
  {
    no: "3",
    name: "Good Health",
    name2: "And Well-Being",
    info: "Promoting mental wellbeing, self-awareness, and personal development through youth-focused programs and digital engagement.",
    image: "/images/sdgs/goal3.jpg",
    bgColor: "#4C9F38",
  },
  {
    no: "4",
    name: "Quality",
    name2: "Education",
    info: "Delivering practical learning through school outreach, skills training, mentorship, and knowledge-sharing platforms.",
    image: "/images/sdgs/goal4.jpg",
    bgColor: "#CA212F",
  },
  {
    no: "5",
    name: "Gender",
    name2: "Equality",
    info: "Empowering girls and young women through the SHINE PRINCESS initiative and amplifying their voices via storytelling.",
    image: "/images/sdgs/goal5.jpg",
    bgColor: "#FF3A21",
  },
  {
    no: "8",
    name: "Decent Work And",
    name2: "Economic Growth",
    info: "Supporting youth skills, entrepreneurship, and eco-craft initiatives while raising awareness on economic empowerment.",
    image: "/images/sdgs/goal8.jpg",
    bgColor: "#A21942",
  },
  {
    no: "10",
    name: "Reduced",
    name2: "Inequalities",
    info: "Promoting the inclusion of marginalized groups, including women and persons with disabilities, through inclusive programming.",
    image: "/images/sdgs/goal10.jpg",
    bgColor: "#E11484",
  },
  {
    no: "13",
    name: "Climate",
    name2: "Action",
    info: "Driving climate education, environmental campaigns, and youth-led waste-to-value innovations.",
    image: "/images/sdgs/goal13.jpg",
    bgColor: "#3F7E44",
  },
  {
    no: "16",
    name: "Peace, Justice And",
    name2: "Strong Institutions",
    info: "Fostering peacebuilding, inclusion, responsible citizenship, and dialogue through school programs.",
    image: "/images/sdgs/goal16.jpg",
    bgColor: "#00689D",
  },
];
</script>

<style lang="scss" scoped>
.sdgSection {
  margin-top: 50px;
  padding: 15px;

  @include respond-to("md") {
    padding: 15px 50px;
  }

  @include respond-to("xl") {
    padding: 25px 100px;
  }

  .heading {
    margin-bottom: 40px;

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
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;

    @include respond-to("md") {
      grid-template-columns: repeat(2, 1fr);
    }

    @include respond-to("lg") {
      grid-template-columns: repeat(3, 1fr);
    }

    @include respond-to("xl") {
      grid-template-columns: repeat(4, 1fr);
      > :last-child {
        grid-column: span 2;
      }
    }

    .sdg-card {
      padding: 24px;
      border-radius: 12px;
      color: #ffffff;
      display: flex;
      flex-direction: column;
      gap: 16px;

      .card-header {
        display: flex;
        flex-direction: column;
        gap: 15px;
        border-bottom: 1px solid #ffffff33;
        padding-bottom: 16px;

        .span {
          display: flex;
          align-items: center;
          gap: 15px;
          font-family: $alternate-font;
          font-size: 18px;
          font-weight: bold;
          span {
            font-size: 42px;
          }
          h3 {
            font-family: $alternate-font;
          }
        }

        .icon {
          width: 100px;
          height: 60px;
          display: flex;
          align-items: center;
          justify-content: center;

          img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            object-position: left;
          }
        }

        h3 {
          font-size: 18px;
          font-weight: 600;
          margin: 0;
          line-height: 1.3;
        }
      }

      .card-body {
        p {
          font-size: 15px;
          line-height: 1.6;
          margin: 0;
          opacity: 0.95;
        }
      }
    }
  }
}
</style>