<template>
  <div class="mvv">
    <div class="mv">
      <div class="box">
        <i class="bi-eye"></i>
        <h3>Vision</h3>
        <p>
          To raise a generation of purpose-driven young leaders equipped with
          the skills, knowledge, and courage to drive social development,
          environmental sustainability, and positive change.
        </p>
      </div>
      <div class="box">
        <i class="bi-bullseye"></i>
        <h3>Mission</h3>
        <p>
          To empower young people to discover their purpose and transform it
          into action by equipping them with life skills, digital and vocational
          competencies, and practical knowledge of social and environmental
          challenges.
        </p>
      </div>
    </div>
    <div class="values">
      <div class="values-header">
        <i class="bi-gem"></i>
        <h3>Core Values</h3>
      </div>
      <div class="values-list">
        <div class="value-item" v-for="(item, index) in values" :key="index">
          <i :class="item.icon"></i>
          <div class="value-text">
            <h4>{{ item.title }}</h4>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const values = ref([
  {
    icon: "bi-person-hearts",
    title: "Purpose-Driven Youth Empowerment",
    description:
      "We believe every young person carries unique potential, skills, and purpose. We empower young people with the knowledge, confidence, opportunities, and support systems needed to become leaders and changemakers.",
  },
  {
    icon: "bi-tree",
    title: "Sustainability & Environmental Stewardship",
    description:
      "We promote environmental responsibility, climate action, and sustainable practices that protect communities and future generations.",
  },
  {
    icon: "bi-people",
    title: "Leadership & Service",
    description:
      "We cultivate responsible leadership by encouraging young people to use their voices, skills, and influence in service to their communities and society.",
  },
  {
    icon: "bi-universal-access",
    title: "Inclusion, Equity & Dignity",
    description:
      "We are committed to creating safe and inclusive spaces where girls, young women, boys, and vulnerable groups, including persons with disabilities, are valued, empowered, and given equal opportunities to thrive.",
  },
  {
    icon: "bi-lightbulb",
    title: "Innovation & Problem Solving",
    description:
      "We encourage creativity, critical thinking, and the use of skills and ideas to address social challenges and create meaningful opportunities.",
  },
  {
    icon: "bi-diagram-3",
    title: "Collaboration & Community Transformation",
    description:
      "We believe lasting impact happens through partnerships and collective action that empower communities and drive sustainable change.",
  },
  {
    icon: "bi-shield-check",
    title: "Integrity & Accountability",
    description:
      "We uphold honesty, transparency, professionalism, and responsibility in all our actions, partnerships, and commitments.",
  },
]);
</script>

<style lang="scss">
.aboutPage {
  .mvv {
    margin: 20px;
    padding: 20px;
    background: $secondary-color;
    border-radius: 16px;

    @include respond-to("md") {
      margin: 35px;
      padding: 50px;
    }

    @include respond-to("xl") {
      max-width: 1200px;
      margin: 60px auto; 
      padding: 70px;
    }

    .mv {
      position: relative;
      display: flex;
      flex-direction: column;
      gap: 25px;

      .box {
        display: flex;
        flex-direction: column;
        gap: 8px;
        color: $background-color;
        i {
          font-size: 48px;
          height: 48px;
          color: $brand-color-3;
        }
        h3 {
          font-family: $alternate-font;
          font-size: 24px;
        }
        p {
          font-family: "Montserrat", sans-serif;
          font-size: 14px;
        }
      }

      @include respond-to("md") {
        flex-direction: row;
        gap: 35px;
        .box {
          width: 50%;
        }
      }

      @include respond-to("xl") {
        gap: 60px;
        .box {
          h3 {
            font-size: 28px;
          }
          p {
            font-size: 16px;
            line-height: 1.6;
          }
        }
      }
    }

    .values {
      margin-top: 25px;
      display: flex;
      flex-direction: column;
      gap: 10px;
      color: $background-color;

      @include respond-to("xl") {
        margin-top: 50px;
      }

      .values-header {
        display: flex;
        flex-direction: column;

        i {
          font-size: 48px;
          height: 48px;
          color: $brand-color-3;
        }

        h3 {
          margin-top: 8px;
          font-family: $alternate-font;
          font-size: 24px;

          @include respond-to("xl") {
            font-size: 28px;
          }
        }
      }

      .values-list {
        display: flex;
        flex-direction: column;
        gap: 15px;
        margin-top: 10px;

        .value-item {
          display: flex;
          gap: 15px;
          align-items: flex-start;

          i {
            font-size: 18px;
            height: 18px;
            color: $brand-color-3;
            margin-top: 2px;
            
            @include respond-to("xl") {
              font-size: 22px;
              height: 22px;
            }
          }

          .value-text {
            display: flex;
            flex-direction: column;
            gap: 6px;

            h4 {
              font-family: $alternate-font;
              font-size: 18px;
              margin: 0;

              @include respond-to("xl") {
                font-size: 20px;
              }
            }

            p {
              font-family: "Montserrat", sans-serif;
              font-size: 12px;

              @include respond-to("xl") {
                font-size: 14px;
                line-height: 1.6;
              }
            }
          }
        }
      }

      @include respond-to("md") {
        .values-list {
          display: grid;
          grid-template-columns: repeat(2, 1fr);
          .value-item {
            padding-right: 25px;
          }
        }
      }

      @include respond-to("xl") {
        .values-list {
          grid-template-columns: repeat(3, 1fr);
          gap: 30px;
          margin-top: 25px;
          
          .value-item {
            padding-right: 0; 
          }
        }
      }
    }
  }
}
</style>