<template>
  <div class="approachSection">
    <div class="intro">
      <i class="bi-asterisk"></i>
      <p>Our Approach &amp; Thematic Areas</p>
    </div>

    <div class="approach">
      <div class="approach-header">
        <h2>Our Approach</h2>
        <p class="approach-sub">
          PVYF utilizes a holistic youth empowerment model built around a
          defined pathway — each step intentionally building on the last.
        </p>
      </div>

      <div class="process-track">
        <div
          v-for="(item, index) in approach"
          :key="item.no"
          class="process-step"
        >
          <!-- Connector line (before each step except the first) -->
          <div v-if="index !== 0" class="connector">
            <div class="connector-line">
              <div class="connector-dot"></div>
              <div class="connector-dot"></div>
              <div class="connector-dot"></div>
            </div>
            <i class="bi-chevron-right connector-arrow"></i>
          </div>

          <!-- Step card -->
          <div class="step-card">
            <div class="step-badge">
              <span class="step-number">{{ item.no }}</span>
            </div>
            <div class="step-icon-wrap">
              <i :class="item.icon"></i>
            </div>
            <div class="step-body">
              <h3 class="step-title">{{ item.info }}</h3>
              <p class="step-desc">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="theme">
      <div class="theme-header">
        <h2>Our Thematic Areas</h2>
        <p class="theme-sub">
          Our work operates at the intersection of several key thematic areas:
        </p>
      </div>

      <div class="theme-grid">
        <div
          v-for="(item, index) in theme"
          :key="index"
          class="theme-card"
        >
          <div class="theme-icon-wrap">
            <i :class="item.icon"></i>
          </div>
          <h3 class="theme-title">{{ item.title }}</h3>
          <p class="theme-info">{{ item.info }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const approach = [
  {
    no: "01",
    info: "Purpose",
    icon: "bi-compass",
    desc: "Helping youth discover their unique calling and the drive to pursue it with conviction.",
  },
  {
    no: "02",
    info: "Skills",
    icon: "bi-tools",
    desc: "Equipping young people with life, digital, and vocational competencies for the real world.",
  },
  {
    no: "03",
    info: "Sustainable Solutions",
    icon: "bi-recycle",
    desc: "Channelling skills into innovative ideas that address social and environmental challenges.",
  },
  {
    no: "04",
    info: "Sustainable Income",
    icon: "bi-graph-up-arrow",
    desc: "Translating solutions into lasting economic opportunities that create community impact.",
  },
];

const theme = [
  { title: 'Leadership and Life Skills Development', icon: 'bi-person-badge', info: 'Focusing on purpose discovery, communication, emotional intelligence, and civic responsibility.' },
  { title: 'Practical Skills & Livelihood Development', icon: 'bi-cpu', info: 'Providing training in vocational skills, AI, digital skills, financial literacy, and entrepreneurship.' },
  { title: 'Environmental Sustainability & Climate Action', icon: 'bi-globe-americas', info: 'Championing eco-craft, waste-to-value innovation, sustainable living, and environmental conservation.' },
  { title: 'Youth Innovation & Community Engagement', icon: 'bi-rocket-takeoff', info: 'Driving social innovation, volunteerism, and youth-led solutions.' },
  { title: 'Mentorship & Opportunity Access', icon: 'bi-binoculars', info: 'Connecting youth with scholarships, professional development, and digital storytelling platforms like podcasts.' },
]
</script>

<style lang="scss">
.aboutPage {
  .approachSection {
    padding: 30px 15px 50px;

    @include respond-to("md") {
      padding: 40px 35px 70px;
    }

    @include respond-to("xl") {
      max-width: 1200px;
      margin: 0 auto;
      padding: 50px 0 80px;
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

    .approach {
      margin-top: 15px;

      .approach-header {
        margin-bottom: 50px;

        h2 {
          font-family: $header-font;
          color: $text-color;
          margin-bottom: 10px;

          @include respond-to("md") {
            font-size: 32px;
          }
        }

        .approach-sub {
          font-size: 14px;
          color: $text-color;
          max-width: 560px;
          line-height: 1.6;

          @include respond-to("xl") {
            font-size: 16px;
          }
        }
      }

      /* ─── Process track ─────────────────────── */
      .process-track {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 0;

        @include respond-to("md") {
          flex-direction: row;
          align-items: stretch;
          gap: 5px;

          & > :nth-child(3) {
            margin-top: 25px;
          }

          & > :nth-child(4) {
            margin-top: 50px;
          }
        }

        @include respond-to("xl") {
          gap: 15px;

          & > :nth-child(3) {
            margin-top: 35px;
          }

          & > :nth-child(4) {
            margin-top: 70px;
          }
        }
      }

      /* ─── Connector (between steps) ─────────── */
      .connector {
        display: flex;
        align-items: center;
        padding: 0 0 0 36px; // indent to align with step card centre on mobile
        height: 56px;

        @include respond-to("md") {
          flex-direction: column;
          padding: 0;
          height: auto;
          width: 40px;
          justify-content: center;
          align-self: center;
          padding-bottom: 24px; // align with card icons visually
        }

        .connector-line {
          display: flex;
          flex-direction: column;
          align-items: center;
          gap: 5px;

          @include respond-to("md") {
            flex-direction: row;
            gap: 5px;
          }

          .connector-dot {
            width: 5px;
            height: 5px;
            border-radius: 50%;
            background: $brand-color-1;
            opacity: 0.35;

            &:nth-child(2) {
              opacity: 0.6;
            }
            &:nth-child(3) {
              opacity: 0.9;
            }
          }
        }

        .connector-arrow {
          font-size: 16px;
          color: $brand-color-1;
          margin-left: 4px;
          transform: rotate(90deg);
          transition: transform 0.3s ease;

          @include respond-to("md") {
            transform: rotate(0deg);
            margin-left: 4px;
          }
        }
      }

      /* ─── Step card ─────────────────────────── */
      .step-card {
        position: relative;
        display: flex;
        flex-direction: row;
        align-items: flex-start;
        gap: 16px;
        background: #fff;
        border-radius: 16px;
        padding: 22px 20px;
        box-shadow: 0 4px 20px rgba(105, 65, 138, 0.1);
        border: 1.5px solid rgba(105, 65, 138, 0.12);
        transition: box-shadow 0.3s ease, transform 0.3s ease,
          border-color 0.3s ease;
        cursor: default;

        @include respond-to("md") {
          flex-direction: column;
          align-items: flex-start;
          gap: 12px;
          flex: 1;
          max-width: 220px;
        }

        @include respond-to("xl") {
          padding: 28px 24px;
          max-width: 260px;
        }

        &:hover {
          transform: translateY(-4px);
          box-shadow: 0 12px 36px rgba(105, 65, 138, 0.18);
          border-color: $brand-color-1;
        }

        .step-badge {
          position: absolute;
          top: -14px;
          left: 20px;
          background: $brand-color-1;
          color: #fff;
          font-family: $alternate-font;
          font-size: 11px;
          font-weight: 700;
          letter-spacing: 1px;
          padding: 3px 10px;
          border-radius: 20px;

          @include respond-to("md") {
            left: 20px;
          }
        }

        .step-icon-wrap {
          flex-shrink: 0;
          width: 48px;
          height: 48px;
          border-radius: 12px;
          background: rgba(105, 65, 138, 0.1);
          display: flex;
          align-items: center;
          justify-content: center;
          transition: background 0.3s ease;

          i {
            font-size: 22px;
            color: $brand-color-1;
          }
        }

        &:hover .step-icon-wrap {
          background: $brand-color-1;
          i {
            color: #fff;
          }
        }

        .step-body {
          display: flex;
          flex-direction: column;
          gap: 6px;

          .step-title {
            font-family: $alternate-font;
            font-size: 16px;
            font-weight: 700;
            color: $text-color;
            margin: 0;
            padding-top: 6px; // leave space for the badge

            @include respond-to("xl") {
              font-size: 18px;
            }
          }

          .step-desc {
            font-family: "Montserrat", sans-serif;
            font-size: 12px;
            color: $text-color;
            opacity: 0.65;
            line-height: 1.55;
            margin: 0;

            @include respond-to("xl") {
              font-size: 13px;
            }
          }
        }
      }
    }

    /* ─── Thematic Areas ──────────────────── */
    .theme {
      margin-top: 45px;

      @include respond-to("xl") {
        margin-top: 90px;
      }

      .theme-header {
        margin-bottom: 20px;

        h2 {
          font-family: $header-font;
          color: $text-color;
          margin-bottom: 10px;

          @include respond-to("md") {
            font-size: 32px;
          }
        }

        .theme-sub {
          font-size: 14px;
          color: $text-color;
          max-width: 520px;
          line-height: 1.6;

          @include respond-to("xl") {
            font-size: 16px;
          }
        }
      }

      /* ─── Card grid ─────────────────────── */
      .theme-grid {
        display: grid;
        grid-template-columns: 1fr;
        gap: 20px;

        @include respond-to("md") {
          grid-template-columns: repeat(2, 1fr);
          gap: 24px;
        }

        @include respond-to("xl") {
          grid-template-columns: repeat(3, 1fr);
          gap: 28px;

          /* centre the last two cards when there are 5 items */
          & > :nth-child(4) {
            grid-column: 1 / 2;
            margin-left: auto;
            margin-right: 0;
            width: calc(100% - 14px);
          }
          & > :nth-child(5) {
            grid-column: 2 / 4;
            margin-left: 0;
            margin-right: auto;
            width: calc(50% - 0px);
          }
        }
      }

      /* ─── Individual card ────────────────── */
      .theme-card {
        position: relative;
        background: #fff;
        border-radius: 18px;
        padding: 30px 24px 26px;
        border: 1.5px solid rgba(105, 65, 138, 0.1);
        box-shadow: 0 4px 24px rgba(105, 65, 138, 0.07);
        transition: transform 0.35s cubic-bezier(0.22, 1, 0.36, 1),
                    box-shadow 0.35s cubic-bezier(0.22, 1, 0.36, 1),
                    border-color 0.3s ease;
        overflow: hidden;
        cursor: default;

        /* decorative left accent bar */
        &::before {
          content: "";
          position: absolute;
          top: 16px;
          left: 0;
          width: 4px;
          height: 48px;
          border-radius: 0 4px 4px 0;
          background: $brand-color-1;
          opacity: 0;
          transition: opacity 0.3s ease, height 0.4s ease;
        }

        /* alternate accent colours */
        &:nth-child(2)::before { background: $brand-color-2; }
        &:nth-child(3)::before { background: $brand-color-3; }
        &:nth-child(4)::before { background: $brand-color-2; }
        &:nth-child(5)::before { background: $brand-color-1; }

        &:hover {
          transform: translateY(-6px);
          box-shadow: 0 16px 48px rgba(105, 65, 138, 0.16);
          border-color: rgba(105, 65, 138, 0.25);

          &::before {
            opacity: 1;
            height: calc(100% - 32px);
          }
        }

        /* icon circle */
        .theme-icon-wrap {
          width: 52px;
          height: 52px;
          border-radius: 14px;
          display: flex;
          align-items: center;
          justify-content: center;
          margin-bottom: 18px;
          background: linear-gradient(135deg, rgba(105, 65, 138, 0.12), rgba(105, 65, 138, 0.04));
          transition: background 0.3s ease, transform 0.3s ease;

          i {
            font-size: 24px;
            color: $brand-color-1;
            transition: color 0.3s ease, transform 0.3s ease;
          }
        }

        /* alternate icon bg tints */
        &:nth-child(2) .theme-icon-wrap {
          background: linear-gradient(135deg, rgba($brand-color-2, 0.12), rgba($brand-color-2, 0.04));
          i { color: $brand-color-2; }
        }
        &:nth-child(3) .theme-icon-wrap {
          background: linear-gradient(135deg, rgba($brand-color-3, 0.14), rgba($brand-color-3, 0.05));
          i { color: darken($brand-color-3, 8%); }
        }
        &:nth-child(4) .theme-icon-wrap {
          background: linear-gradient(135deg, rgba($brand-color-2, 0.12), rgba($brand-color-2, 0.04));
          i { color: $brand-color-2; }
        }
        &:nth-child(5) .theme-icon-wrap {
          background: linear-gradient(135deg, rgba($brand-color-1, 0.12), rgba($brand-color-1, 0.04));
          i { color: $brand-color-1; }
        }

        &:hover .theme-icon-wrap {
          transform: scale(1.08);
        }

        .theme-title {
          font-family: $alternate-font;
          font-size: 17px;
          font-weight: 700;
          color: $text-color;
          margin: 0 0 8px;
          line-height: 1.35;

          @include respond-to("xl") {
            font-size: 19px;
          }
        }

        .theme-info {
          font-family: "Montserrat", sans-serif;
          font-size: 12.5px;
          color: $text-color;
          opacity: 0.6;
          line-height: 1.6;
          margin: 0;

          @include respond-to("xl") {
            font-size: 14px;
          }
        }
      }
    }
  }
}
</style>