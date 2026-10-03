<template>
  <div class="volunteerUnits">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Our Volunteering Units</p>
      </div>
      <h2>Find Your Place in the Movement</h2>
      <p class="subtitle">
        PVYF volunteers are organized into specialized units, each playing a critical role in delivering our mission.
      </p>
    </div>

    <div class="units-grid">
      <div
        v-for="(unit, index) in units"
        :key="unit.name"
        class="unit-card"
        :class="{ 'expanded': expandedIndex === index && isMobile }"
        @click="handleCardClick(index)"
      >
        <div class="card-header">
          <div class="icon-ring" :style="{ '--accent': unit.color }">
            <i :class="unit.icon"></i>
          </div>
          <h3>{{ unit.name }}</h3>
          <i class="bi-chevron-down chevron"></i>
        </div>
        <div class="card-body">
          <p>{{ unit.description }}</p>
          <ul>
            <li v-for="task in unit.tasks" :key="task">{{ task }}</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const expandedIndex = ref(null)
const isMobile = ref(true)
const MD_BREAKPOINT = 600

const checkMobile = () => {
  isMobile.value = window.innerWidth < MD_BREAKPOINT
  if (!isMobile.value) expandedIndex.value = null
}

const handleCardClick = (index) => {
  if (!isMobile.value) return
  expandedIndex.value = expandedIndex.value === index ? null : index
}

onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile)
})

const units = [
  {
    name: 'Operations & Administration',
    icon: 'bi-gear-wide-connected',
    color: '#69418A',
    description: 'The backbone of the Foundation. This unit ensures smooth planning, logistics, and coordination across all PVYF activities and programmes.',
    tasks: [
      'Planning and logistics for events and programmes',
      'Internal coordination and administrative support',
      'Record keeping and organizational management',
      'Venue and resource management'
    ]
  },
  {
    name: 'Media & Communications',
    icon: 'bi-camera-reels',
    color: '#D32C24',
    description: 'The storytelling arm of PVYF. This unit captures, creates, and shares the Foundation\'s work across digital and traditional media platforms.',
    tasks: [
      'Photography and videography at events',
      'Social media management and content creation',
      'Press releases and media liaison',
      'Graphic design and branding materials'
    ]
  },
  {
    name: 'Monitoring, Evaluation & Reporting',
    icon: 'bi-clipboard-data',
    color: '#E9A63B',
    description: 'The insight engine. This unit tracks progress, evaluates impact, and generates the data that guides our strategic direction.',
    tasks: [
      'Data collection and feedback analysis',
      'Impact tracking and programme evaluation',
      'Report writing and documentation',
      'Survey design and beneficiary follow-up'
    ]
  },
  {
    name: 'Community Engagement & Partnerships',
    icon: 'bi-people',
    color: '#69418A',
    description: 'The relationship builders. This unit connects PVYF with communities, stakeholders, partners, and support systems that amplify our reach.',
    tasks: [
      'Community mobilization and outreach',
      'Partnership development and liaison',
      'Stakeholder engagement and networking',
      'Fundraising and resource mobilization support'
    ]
  },
  {
    name: 'Training & Facilitation',
    icon: 'bi-mortarboard',
    color: '#D32C24',
    description: 'The capacity builders. This unit designs and delivers impactful training sessions, workshops, and facilitation experiences for youth beneficiaries.',
    tasks: [
      'Workshop facilitation and moderation',
      'Curriculum development and training design',
      'Mentorship and skills coaching',
      'Youth engagement and activity coordination'
    ]
  },
  {
    name: 'Volunteer Coordination',
    icon: 'bi-heart-pulse',
    color: '#E9A63B',
    description: 'The people champions. This unit manages volunteer recruitment, onboarding, welfare, and development to ensure every volunteer thrives.',
    tasks: [
      'Volunteer recruitment and onboarding',
      'Team building and welfare management',
      'Volunteer performance tracking',
      'Recognition programmes and motivation'
    ]
  }
]
</script>

<style lang="scss" scoped>
.volunteerUnits {
  padding: 40px 15px;
  background: $primary-color;

  @include respond-to("md") {
    padding: 60px 50px;
  }

  @include respond-to("xl") {
    padding: 70px 100px;
  }

  .heading {
    max-width: 700px;
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
      margin-bottom: 12px;
      line-height: 1.2;

      @include respond-to("md") {
        font-size: 32px;
      }
    }

    .subtitle {
      font-size: 15px;
      line-height: 1.6;
      opacity: 0.85;
    }

    @include respond-to("xl") {
      margin-bottom: 50px;
    }
  }

  .units-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
    max-width: 1100px;
    margin: 0 auto;

    @include respond-to("md") {
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    @include respond-to("xl") {
      grid-template-columns: repeat(3, 1fr);
    }

    .unit-card {
      background: $background-color;
      border-radius: 16px;
      overflow: hidden;
      cursor: pointer;
      transition: box-shadow 0.35s ease, transform 0.35s ease;
      border: 1px solid transparent;

      @include respond-to("md") {
        cursor: default;
      }

      &:hover {
        box-shadow: 0 8px 30px rgba($brand-color-1, 0.12);
        transform: translateY(-3px);
        border-color: rgba($brand-color-1, 0.15);
      }

      &.expanded {
        border-color: rgba($brand-color-1, 0.25);
        box-shadow: 0 8px 30px rgba($brand-color-1, 0.12);

        .card-header .chevron {
          transform: rotate(180deg);
        }

        .card-body {
          max-height: 400px;
          padding: 0 20px 20px;
          opacity: 1;
        }
      }

      .card-header {
        display: flex;
        align-items: center;
        gap: 14px;
        padding: 20px;

        .icon-ring {
          flex-shrink: 0;
          width: 48px;
          height: 48px;
          border-radius: 50%;
          display: flex;
          align-items: center;
          justify-content: center;
          background: rgba($brand-color-1, 0.1);
          border: 2px solid var(--accent, $brand-color-1);
          transition: background 0.3s ease;

          i {
            font-size: 20px;
            color: var(--accent, $brand-color-1);
          }
        }

        h3 {
          flex: 1;
          font-family: $alternate-font;
          font-size: 15px;
          font-weight: 700;
          line-height: 1.3;

          @include respond-to("md") {
            font-size: 16px;
          }
        }

        .chevron {
          font-size: 16px;
          color: $brand-color-1;
          transition: transform 0.35s ease;

          @include respond-to("md") {
            display: none;
          }
        }
      }

      .card-body {
        max-height: 0;
        padding: 0 20px;
        opacity: 0;
        overflow: hidden;
        transition: max-height 0.45s cubic-bezier(0.4, 0, 0.2, 1),
                    padding 0.45s cubic-bezier(0.4, 0, 0.2, 1),
                    opacity 0.35s ease;

        @include respond-to("md") {
          max-height: none;
          padding: 0 20px 20px;
          opacity: 1;
          overflow: visible;
        }

        p {
          font-size: 14px;
          line-height: 1.65;
          margin-bottom: 14px;
          opacity: 0.85;
        }

        ul {
          list-style: none;
          padding: 0;
          margin: 0;
          display: flex;
          flex-direction: column;
          gap: 8px;

          li {
            font-size: 13px;
            line-height: 1.5;
            padding-left: 18px;
            position: relative;

            &::before {
              content: '';
              position: absolute;
              left: 0;
              top: 7px;
              width: 8px;
              height: 8px;
              border-radius: 50%;
              background: $brand-color-1;
              opacity: 0.6;
            }
          }
        }
      }

      &:hover .card-header .icon-ring {
        background: rgba($brand-color-1, 0.18);
      }
    }
  }
}
</style>
