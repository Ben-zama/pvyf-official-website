<template>
  <div class="volunteerBenefits">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Why Volunteer With PVYF?</p>
      </div>
      <h2>The Benefits of Joining Our Team</h2>
    </div>

    <div class="benefits-grid">
      <div
        v-for="(benefit, index) in benefits"
        :key="benefit.title"
        class="benefit-card"
        :style="{ '--delay': index * 0.05 + 's' }"
      >
        <div class="card-number">{{ String(index + 1).padStart(2, '0') }}</div>
        <div class="card-icon">
          <i :class="benefit.icon"></i>
        </div>
        <h3>{{ benefit.title }}</h3>
        <p>{{ benefit.description }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const benefits = [
  {
    title: 'Skill Development',
    icon: 'bi-rocket-takeoff',
    description: 'Gain hands-on experience in event management, media production, facilitation, research, community mobilization, and project coordination.'
  },
  {
    title: 'Leadership Exposure',
    icon: 'bi-trophy',
    description: 'Take on meaningful responsibilities, lead teams, manage projects, and develop your capacity as a future-ready young leader.'
  },
  {
    title: 'Networking Opportunities',
    icon: 'bi-globe2',
    description: 'Connect with like-minded young people, industry professionals, mentors, partner organizations, and community leaders.'
  },
  {
    title: 'Certificate of Service',
    icon: 'bi-award',
    description: 'Receive an official certificate of volunteer service recognizing your contribution and commitment to community development.'
  },
  {
    title: 'Mentorship Access',
    icon: 'bi-compass',
    description: 'Benefit from structured mentorship and guidance from experienced PVYF team members and external resource persons.'
  },
  {
    title: 'Personal Growth',
    icon: 'bi-graph-up-arrow',
    description: 'Build confidence, discover your purpose, strengthen communication skills, and develop a strong sense of social responsibility.'
  },
  {
    title: 'Community Impact',
    icon: 'bi-heart',
    description: 'Directly contribute to transforming lives and communities through youth empowerment, education, and sustainability projects.'
  },
  {
    title: 'Training & Workshops',
    icon: 'bi-journal-bookmark',
    description: 'Access exclusive training sessions, capacity-building workshops, and professional development opportunities as a PVYF volunteer.'
  }
]
</script>

<style lang="scss" scoped>
.volunteerBenefits {
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
    max-width: 600px;
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

  .benefits-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;

    @include respond-to("md") {
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
    }

    @include respond-to("xl") {
      grid-template-columns: repeat(4, 1fr);
    }

    .benefit-card {
      position: relative;
      padding: 28px 24px;
      border-radius: 16px;
      background: $primary-color;
      border: 1px solid transparent;
      overflow: hidden;
      transition: transform 0.35s ease, box-shadow 0.35s ease, border-color 0.35s ease;

      &::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 3px;
        background: linear-gradient(90deg, $brand-color-1, $brand-color-2, $brand-color-3);
        opacity: 0;
        transition: opacity 0.35s ease;
      }

      &:hover {
        transform: translateY(-4px);
        box-shadow: 0 12px 32px rgba($brand-color-1, 0.1);
        border-color: rgba($brand-color-1, 0.12);

        &::before {
          opacity: 1;
        }

        .card-number {
          opacity: 0.08;
        }

        .card-icon i {
          transform: scale(1.15);
          color: $brand-color-2;
        }
      }

      .card-number {
        position: absolute;
        top: 12px;
        right: 16px;
        font-family: $header-font;
        font-size: 48px;
        opacity: 0.05;
        line-height: 1;
        transition: opacity 0.35s ease;
        user-select: none;
      }

      .card-icon {
        margin-bottom: 16px;

        i {
          font-size: 28px;
          color: $brand-color-1;
          transition: transform 0.35s ease, color 0.35s ease;
        }
      }

      h3 {
        font-family: $alternate-font;
        font-size: 16px;
        font-weight: 700;
        margin-bottom: 10px;
        line-height: 1.3;
      }

      p {
        font-size: 13.5px;
        line-height: 1.65;
        opacity: 0.8;
      }
    }
  }
}
</style>
