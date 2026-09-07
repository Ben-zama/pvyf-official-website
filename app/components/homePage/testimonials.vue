<template>
  <div class="testimonialSection">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Testimonials</p>
      </div>
      <h2>Selected Voices From Our Community</h2>
      <p>
        Hear from the young leaders, educators, and partners transforming their
        communities through our programs.
      </p>
    </div>

    <div class="slider-container">
      <swiper
        :modules="modules"
        :slidesPerView="1"
        :spaceBetween="20"
        :centeredSlides="true"
        :loop="true"
        :loopedSlides="testimonials.length"
        :pagination="{ clickable: true }"
        :autoplay="{ delay: 5000, disableOnInteraction: false }"
        :breakpoints="{
          '768': {
            slidesPerView: 2,
            spaceBetween: 30,
          },
          '1280': {
            slidesPerView: 4,
            spaceBetween: 30,
          },
        }"
        class="testimonial-swiper"
      >
        <swiper-slide v-for="testimonial in testimonials" :key="testimonial.id">
          <div class="testimonial-card">
            <div class="quote-icon">
              <i class="bi bi-quote"></i>
            </div>
            <p class="quote-text">"{{ testimonial.quote }}"</p>

            <div class="author-info">
              <h4>{{ testimonial.author }}</h4>
              <p class="role">{{ testimonial.role }}</p>
              <p class="organization">{{ testimonial.organization }}</p>
              <span class="program-tag">{{ testimonial.program }}</span>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination, Autoplay } from "swiper/modules";

// Import Swiper styles
import "swiper/css";
import "swiper/css/pagination";

const modules = [Pagination, Autoplay];

const testimonials = [
  {
    id: 1,
    quote:
      "Before the foundation visited our school, I didn't know much about the Sustainable Development Goals. The outreach opened my eyes to how small actions can create big changes. Working with my classmates on our 'Peace Begins With Me' project helped me realize that I have a voice and a role to play in my community.",
    author: "Grace O.",
    role: "Student",
    organization: "Milton College of Arts and Sciences",
    program: "WAKE UP School Outreach Program",
  },
  {
    id: 2,
    quote:
      "The two-week training completely changed my mindset. I learned how to turn discarded tyres into beautiful center tables and used AI to create videos about proper waste management. I now have practical skills I can use to earn an income while protecting the environment.",
    author: "Emmanuel D.",
    role: "Youth Participant",
    organization: "First Cohort Graduate",
    program: "Work It Out Training Program",
  },
  {
    id: 3,
    quote:
      "Partnering with PVYF has been a tremendous asset to our community. Seeing the students engage so deeply with topics like climate action, mental wellness, and first aid shows the power of their holistic approach. They are truly raising a generation of responsible, solution-oriented leaders.",
    author: "Mrs. Amina Yusuf",
    role: "Facilitator / Partner",
    organization: "Nigerian Red Cross Society",
    program: "PVYF Collaborative Partner",
  },
  {
    id: 4,
    quote:
      "The weekend vocational training has given me the confidence to start my own small business. The continuous mentorship makes sure we are never left behind.",
    author: "Samuel T.",
    role: "Youth Entrepreneur",
    organization: "Community Youth",
    program: "Work It Out Club Series",
  },
  {
    id: 5,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
  {
    id: 6,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
  {
    id: 7,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
  {
    id: 8,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
  {
    id: 9,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
  {
    id: 10,
    quote:
      "Creating digital stories and podcasts about environmental sustainability has amplified our voices beyond our local community. We are no longer just learning; we are advocating.",
    author: "Aisha M.",
    role: "Youth Advocate",
    organization: "Media Volunteer",
    program: "Trailblazer Youths Podcast",
  },
];
</script>

<style lang="scss">
.testimonialSection {
  margin: 50px 0;
  padding: 25px 15px;
  background: $primary-color;

  @include respond-to("md") {
    padding: 50px 15px;
  }

  @include respond-to("xl") {
    padding: 100px 15px;
  }

  .heading {
    margin-bottom: 40px;

    @include respond-to("md") {
      padding: 0 35px;
    }
    @include respond-to("xl") {
      padding: 0 85px;
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
      margin: 10px 0;
      font-size: 26px;
    }

    @include respond-to("md") {
      max-width: 700px;
      h2 {
        font-size: 34px;
      }
    }

    @include respond-to("xl") {
      max-width: 800px;
    }
  }

  .slider-container {
    width: 100%;
    position: relative;

    &::before {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      width: 0;
      background: linear-gradient(
        to right,
        $primary-color 0%,
        transparent 100%
      );
      z-index: 2;
      pointer-events: none;
    }

    &::after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      right: 0;
      width: 0;
      background: linear-gradient(to left, $primary-color 0%, transparent 100%);
      z-index: 2;
      pointer-events: none;
    }

    @include respond-to("md") {
      &::before,
      &::after {
        width: 15%;
      }
    }

    .testimonial-swiper {
      padding-bottom: 50px;

      @include respond-to("xl") {
        padding-bottom: 60px;
      }
    }

    .swiper-slide {
      height: auto;

      @include respond-to("md") {
        &-active {
          .testimonial-card {
            background: rgba($brand-color-1, 0.9);
            .quote-icon {
              color: $brand-color-3;
            }
            .quote-text {
              color: $background-color;
            }
            .author-info {
              border-top-color: rgba($brand-color-3, 0.5);
              h4 {
                color: $background-color;
              }
              .role,
              .organization {
                color: rgba($background-color, 0.7);
              }
              .program-tag {
                color: $brand-color-3;
              }
            }
          }
        }
      }
    }

    .testimonial-card {
      background: $background-color;
      border-radius: 12px;
      padding: 24px;
      height: 100%;
      display: flex;
      flex-direction: column;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);

      .quote-icon {
        font-size: 24px;
        color: $brand-color-1;
        margin-bottom: 15px;
        opacity: 0.8;
      }

      .quote-text {
        font-size: 14px;
        line-height: 1.6;
        margin-bottom: 30px;
        flex-grow: 1;
        font-style: italic;
      }

      .author-info {
        border-top: 1px solid rgba($brand-color-1, 0.3);
        padding-top: 20px;

        h4 {
          margin: 0 0 5px 0;
          font-size: 16px;
        }

        .role,
        .organization {
          margin: 0;
          font-size: 12px;
          color: darken($background-color, 40%);
          line-height: 1.4;
        }

        .program-tag {
          display: inline-block;
          margin-top: 8px;
          font-family: $alternate-font;
          color: $brand-color-1;
          font-size: 10px;
        }
      }
    }

    .swiper-pagination-bullet {
      background-color: darken($background-color, 20%);
      opacity: 1;
      width: 10px;
      height: 10px;
      transition: all 0.3s ease;

      &-active {
        background-color: $brand-color-1;
        width: 25px;
        border-radius: 5px;
      }
    }
  }
}
</style>