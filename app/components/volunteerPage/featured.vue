<template>
  <div class="featuredVolunteer">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Featured Volunteer</p>
      </div>
      <h2>Spotlight: Volunteer of the Hour</h2>
    </div>

    <div class="spotlight-card">
      <div class="image-col">
        <div class="image-wrapper">
          <img
            :src="currentVolunteer.img"
            :alt="currentVolunteer.name"
            :key="currentVolunteer.name"
          />
          <div class="badge">
            <i class="bi-star-fill"></i>
            <span>Featured</span>
          </div>
        </div>
      </div>

      <div class="text-col">
        <div class="quote-mark">
          <i class="bi-quote"></i>
        </div>
        <p class="testimonial">{{ currentVolunteer.quote }}</p>
        <div class="volunteer-info">
          <h3>{{ currentVolunteer.name }}</h3>
          <p class="role">{{ currentVolunteer.role }}</p>
          <p class="unit">{{ currentVolunteer.unit }}</p>
        </div>

        <div class="stats">
          <div class="stat" v-for="stat in currentVolunteer.stats" :key="stat.label">
            <span class="stat-value">{{ stat.value }}</span>
            <span class="stat-label">{{ stat.label }}</span>
          </div>
        </div>

        <div class="timer">
          <i class="bi-clock"></i>
          <span>Next spotlight in {{ timeRemaining }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const volunteers = [
  {
    name: 'Amina Bello',
    img: '/images/volunteers/featured1.png',
    role: 'Lead Facilitator',
    unit: 'Training & Facilitation Unit',
    quote: 'Volunteering with PVYF has been the most transformative experience of my life. I\'ve grown from a shy student into a confident facilitator who can inspire rooms full of young people. Every workshop I lead reminds me why this work matters.',
    stats: [
      { value: '24+', label: 'Workshops Led' },
      { value: '500+', label: 'Youth Impacted' },
      { value: '2 Years', label: 'With PVYF' }
    ]
  },
  {
    name: 'Daniel Okonkwo',
    img: '/images/volunteers/featured2.png',
    role: 'Media Coordinator',
    unit: 'Media & Communications Unit',
    quote: 'Through PVYF, I discovered that storytelling can change the world. Every photo I capture and every video I edit tells the story of a young person whose life is being transformed. This is more than volunteering — it\'s purpose.',
    stats: [
      { value: '100+', label: 'Events Covered' },
      { value: '1,200+', label: 'Content Pieces' },
      { value: '18 Months', label: 'With PVYF' }
    ]
  },
  {
    name: 'Grace Adamu',
    img: '/images/volunteers/featured3.png',
    role: 'Community Liaison',
    unit: 'Community Engagement & Partnerships Unit',
    quote: 'I joined PVYF because I wanted to give back to my community. What I didn\'t expect was how much the community would give back to me. The connections, the growth, the impact — it\'s beyond anything I imagined.',
    stats: [
      { value: '15+', label: 'Communities Reached' },
      { value: '8', label: 'Partnerships Built' },
      { value: '1 Year', label: 'With PVYF' }
    ]
  }
]

const currentHour = ref(new Date().getHours())
const timeRemaining = ref('')
let timerInterval = null

const currentVolunteer = computed(() => {
  const index = currentHour.value % volunteers.length
  return volunteers[index]
})

const updateTimeRemaining = () => {
  const now = new Date()
  const nextHour = new Date(now)
  nextHour.setHours(now.getHours() + 1, 0, 0, 0)
  const diff = nextHour - now
  const minutes = Math.floor(diff / 60000)
  const seconds = Math.floor((diff % 60000) / 1000)
  timeRemaining.value = `${minutes}m ${String(seconds).padStart(2, '0')}s`
  currentHour.value = now.getHours()
}

onMounted(() => {
  updateTimeRemaining()
  timerInterval = setInterval(updateTimeRemaining, 1000)
})

onUnmounted(() => {
  if (timerInterval) clearInterval(timerInterval)
})
</script>

<style lang="scss" scoped>
.featuredVolunteer {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 15px;

  @include respond-to("md") {
    padding: 60px 50px;
  }

  @include respond-to("xl") {
    padding: 70px 100px;
  }

  .heading {
    margin-bottom: 30px;

    .intro {
      display: flex;
      align-items: baseline;
      gap: 10px;
      margin-bottom: 8px;
      i {
        color: $brand-color-1;
        font-size: 14px;
      }
      p {
        font-family: $alternate-font;
        font-size: 14px;
        letter-spacing: 0.5px;
      }
    }

    h2 {
      font-size: 24px;
      line-height: 1.2;

      @include respond-to("md") {
        font-size: 32px;
      }
    }

    @include respond-to("xl") {
      margin-bottom: 50px;
    }
  }

  .spotlight-card {
    display: flex;
    flex-direction: column;
    gap: 25px;
    background: linear-gradient(135deg, rgba($brand-color-1, 0.06) 0%, rgba($brand-color-3, 0.04) 100%);
    border-radius: 20px;
    overflow: hidden;
    border: 1px solid rgba($brand-color-1, 0.1);

    @include respond-to("md") {
      flex-direction: row;
      gap: 0;
    }

    .image-col {
      @include respond-to("md") {
        flex: 0 0 40%;
      }

      .image-wrapper {
        position: relative;
        width: 100%;
        height: 320px;

        @include respond-to("md") {
          height: 100%;
          min-height: 450px;
        }

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          object-position: center top;
        }

        .badge {
          position: absolute;
          top: 16px;
          left: 16px;
          display: flex;
          align-items: center;
          gap: 6px;
          padding: 6px 14px;
          background: $brand-color-3;
          color: white;
          border-radius: 20px;
          font-family: $alternate-font;
          font-size: 12px;
          font-weight: 700;
          letter-spacing: 0.5px;
          box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);

          i {
            font-size: 11px;
          }
        }
      }
    }

    .text-col {
      flex: 1;
      padding: 25px 20px 30px;
      display: flex;
      flex-direction: column;
      justify-content: center;

      @include respond-to("md") {
        padding: 40px 35px;
      }

      .quote-mark {
        margin-bottom: 12px;

        i {
          font-size: 36px;
          color: $brand-color-1;
          opacity: 0.3;
        }
      }

      .testimonial {
        font-size: 16px;
        line-height: 1.75;
        font-style: italic;
        margin-bottom: 24px;
        opacity: 0.9;

        @include respond-to("md") {
          font-size: 17px;
        }
      }

      .volunteer-info {
        margin-bottom: 24px;

        h3 {
          font-family: $alternate-font;
          font-size: 20px;
          font-weight: 800;
          margin-bottom: 4px;
          color: $brand-color-1;
        }

        .role {
          font-family: $alternate-font;
          font-size: 14px;
          font-weight: 600;
          margin-bottom: 2px;
        }

        .unit {
          font-size: 13px;
          opacity: 0.65;
        }
      }

      .stats {
        display: flex;
        gap: 24px;
        margin-bottom: 24px;
        flex-wrap: wrap;

        .stat {
          display: flex;
          flex-direction: column;
          gap: 2px;

          .stat-value {
            font-family: $header-font;
            font-size: 22px;
            color: $brand-color-1;
            line-height: 1;
          }

          .stat-label {
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.8px;
            opacity: 0.6;
            font-family: $alternate-font;
          }
        }
      }

      .timer {
        display: flex;
        align-items: center;
        gap: 8px;
        padding: 10px 16px;
        background: rgba($brand-color-1, 0.08);
        border-radius: 10px;
        width: fit-content;

        i {
          font-size: 14px;
          color: $brand-color-1;
        }

        span {
          font-family: $alternate-font;
          font-size: 12px;
          letter-spacing: 0.5px;
          opacity: 0.7;
        }
      }
    }
  }
}
</style>
