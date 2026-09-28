<template>
  <div class="projectsPage">
    <!-- Intro Section -->
    <section class="projects-intro">
      <div class="intro-badge">
        <i class="bi-asterisk"></i>
        <p>Our Projects</p>
      </div>
      <h2>Programs & Strategic Initiatives</h2>
      <p class="intro-description">
        The Princess Vanessa Yemilo Foundation (PVYF) delivers its mission
        through an integrated ecosystem of youth-centered flagship programs
        designed to move young people from awareness and mindset transformation
        to skills acquisition, leadership development, innovation, advocacy, and
        long-term community impact.
      </p>
    </section>

    <!-- Flagship Projects -->
    <section class="projects-grid">
      <div
        class="project-item"
        v-for="(project, index) in flagship"
        :key="index"
        :class="`project-item--${index + 1}`"
      >
        <div class="project-item__content">
          <span class="project-item__number">{{
            String(index + 1).padStart(2, "0")
          }}</span>
          <h3 class="project-item__title">{{ project.title }}</h3>
          <p class="project-item__description">{{ project.info }}</p>
          <div class="project-item__highlights" v-if="project.highlights">
            <div
              class="highlight"
              v-for="(highlight, hIndex) in project.highlights"
              :key="hIndex"
            >
              <i :class="highlight.icon"></i>
              <span>{{ highlight.text }}</span>
            </div>
          </div>
          <ctaButton :name="'Learn More'" :link="`/projects/${project.slug}`" />
        </div>
        <div class="project-item__visual">
          <div class="project-item__image-wrapper">
            <img :src="project.img" :alt="project.title" />
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="projects-cta">
      <div class="projects-cta__inner">
        <h2>Want to Get Involved?</h2>
        <p>
          Whether you're looking to volunteer, partner, or donate — there's a
          place for you in the PVYF mission. Together, we can empower the next
          generation of changemakers.
        </p>
        <div class="projects-cta__buttons">
          <ctaButton name="Volunteer With Us" link="/volunteer" />
          <ctaButton name="Contact Us" link="/contact" />
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
definePageMeta({
  layout: "page-header",
  title: "Our Projects",
});

const flagship = [
  {
    title: "WakeUp School Outreach",
    slug: "wakeup-school-outreach",
    info: "The WakeUp School Outreach Program is the Princess Vanessa Yemilo Foundation's flagship school-based initiative designed to inspire purpose discovery, leadership development, and social responsibility among secondary school students.",
    img: "/illustrations/wuso.svg",
    highlights: [
      { icon: "bi-mortarboard", text: "Secondary School Students" },
      { icon: "bi-lightning", text: "Purpose Discovery" },
      { icon: "bi-people", text: "Leadership Development" },
    ],
  },
  {
    title: "Work It Out Training Program and Exhibition Day",
    slug: "work-it-out-training",
    info: "The Work It Out Training Program and Exhibition Day is PVYF's annual youth empowerment initiative that provides secondary school students and community youths with practical skills, leadership training, entrepreneurship education, and sustainability knowledge during the long vacation period.",
    img: "/illustrations/wio.svg",
    highlights: [
      { icon: "bi-tools", text: "Practical Skills Training" },
      { icon: "bi-briefcase", text: "Entrepreneurship Education" },
      { icon: "bi-recycle", text: "Sustainability Knowledge" },
    ],
  },
  {
    title: "Work It Out Club Series (WIOCS)",
    slug: "work-it-out-club-series",
    info: "The Work It Out Club Series (SDCS) is a three-month weekend vocational and entrepreneurship program designed to equip young people with practical, income-generating skills that promote self-reliance and sustainable livelihoods.",
    img: "/illustrations/wiocs.svg",
    highlights: [
      { icon: "bi-calendar3", text: "3-Month Weekend Program" },
      { icon: "bi-cash-stack", text: "Income-Generating Skills" },
      { icon: "bi-hand-thumbs-up", text: "Self-Reliance" },
    ],
  },
  {
    title: "Shine Princess Summit",
    slug: "shine-princess-summit",
    info: "An annual girls' leadership and empowerment initiative designed to celebrate progress, strengthen leadership capacity, and inspire young women to become confident changemakers in their communities.",
    img: "/illustrations/sps.svg",
    highlights: [
      { icon: "bi-star", text: "Girls' Leadership" },
      { icon: "bi-graph-up-arrow", text: "Women Empowerment" },
      { icon: "bi-mic", text: "Mentorship & Career Growth" },
    ],
  },
  {
    title: "Trailblazer Youths & Thriving Communities Podcast",
    slug: "trailblazer-youths-podcast",
    info: "A digital media, storytelling, and advocacy initiative dedicated to amplifying youth voices, promoting community-driven solutions, and inspiring positive social change.",
    img: "/illustrations/tytcp.svg",
    highlights: [
      { icon: "bi-camera-video", text: "Digital Storytelling" },
      { icon: "bi-globe", text: "SDGs Advocacy" },
      { icon: "bi-tree", text: "Climate Action" },
    ],
  },
  {
    title: "PVY Foundation Annual Trailblazers Summit",
    slug: "annual-trailblazers-summit",
    info: "The Foundation's annual flagship gathering that brings together young leaders, educators, and stakeholders to celebrate impact, foster collaboration, and advance sustainable development.",
    img: "/illustrations/ats.svg",
    highlights: [
      { icon: "bi-award", text: "Celebrate Impact" },
      { icon: "bi-diagram-3", text: "Multi-Sector Collaboration" },
      { icon: "bi-link-45deg", text: "Strategic Partnerships" },
    ],
  }
];
</script>

<style lang="scss" scoped>
.projectsPage {
  overflow: hidden;
}

/* ─── Intro Section ─── */
.projects-intro {
  padding: 40px 15px 20px;
  max-width: 800px;

  @include respond-to("md") {
    padding: 60px 25px 30px;
  }

  @include respond-to("xl") {
    padding: 80px 100px 40px;
  }

  .intro-badge {
    display: flex;
    align-items: baseline;
    gap: 10px;
    margin-bottom: 12px;
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
    font-size: 28px;
    margin-bottom: 16px;
    line-height: 1.2;

    @include respond-to("md") {
      font-size: 36px;
    }
  }

  .intro-description {
    font-size: 15px;
    line-height: 1.7;
    color: $secondary-color;

    @include respond-to("md") {
      font-size: 16px;
    }
  }
}

/* ─── Projects Grid ─── */
.projects-grid {
  padding: 20px 15px;
  display: flex;
  flex-direction: column;
  gap: 30px;

  @include respond-to("md") {
    padding: 30px 25px;
    gap: 40px;
  }

  @include respond-to("xl") {
    padding: 40px 100px;
    gap: 50px;
  }
}

/* ─── Individual Project Item ─── */
.project-item {
  border-radius: 20px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 25px;
  transition: transform 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94),
    box-shadow 0.4s ease;

  &:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08);
  }

  @include respond-to("md") {
    flex-direction: row;
    align-items: center;
    padding: 40px;
    gap: 40px;

    &:nth-child(even) {
      flex-direction: row-reverse;
    }
  }

  @include respond-to("xl") {
    padding: 60px 50px;
    gap: 60px;
  }

  // Color variants
  &--1, &--4 {
    background: $brand-color-1;
    color: $background-color;

    .project-item__number {
      color: rgba(255, 255, 255, 0.2);
    }
    .highlight {
      background: rgba(255, 255, 255, 0.12);
      color: $background-color;
    }
    :deep(.button) {
      &:hover {
        background: $text-color;
        color: $background-color;
        .button__icon-wrapper {
          background: $background-color;
          color: $text-color;
        }
      }
    }
  }

  &--2, &--5 {
    background: $brand-color-2;

    .project-item__number {
      color: rgba(0, 0, 0, 0.1);
    }
    .highlight {
      background: rgba(0, 0, 0, 0.08);
    }
    :deep(.button) {
      &:hover {
        background: $text-color;
        color: $background-color;
        .button__icon-wrapper {
          background: $background-color;
          color: $text-color;
        }
      }
    }
  }

  &--3, &--6 {
    background: $brand-color-3;

    .project-item__number {
      color: rgba(0, 0, 0, 0.1);
    }
    .highlight {
      background: rgba(0, 0, 0, 0.08);
    }
    :deep(.button) {
      &:hover {
        background: $text-color;
        color: $background-color;
        .button__icon-wrapper {
          background: $background-color;
          color: $text-color;
        }
      }
    }
  }

  /* ── Content Side ── */
  &__content {
    flex: 1.2;
    display: flex;
    flex-direction: column;
    align-items: start;
    gap: 16px;
  }

  &__number {
    font-family: $alternate-font;
    font-size: 64px;
    font-weight: 900;
    line-height: 1;
    letter-spacing: -2px;
    user-select: none;

    @include respond-to("md") {
      font-size: 80px;
    }

    @include respond-to("xl") {
      font-size: 96px;
    }
  }

  &__title {
    font-size: 22px;
    font-weight: 700;
    line-height: 1.3;

    @include respond-to("md") {
      font-size: 26px;
    }

    @include respond-to("xl") {
      font-size: 30px;
    }
  }

  &__description {
    font-size: 14px;
    line-height: 1.7;
    opacity: 0.9;

    @include respond-to("md") {
      font-size: 15px;
    }
  }

  /* ── Highlights ── */
  &__highlights {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin: 8px 0;

    .highlight {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 8px 14px;
      border-radius: 100px;
      font-family: $alternate-font;
      font-size: 12px;
      letter-spacing: 0.3px;
      transition: transform 0.2s ease;

      &:hover {
        transform: scale(1.05);
      }

      i {
        font-size: 14px;
      }

      @include respond-to("md") {
        font-size: 13px;
        padding: 10px 16px;
      }
    }
  }

  /* ── Visual Side ── */
  &__visual {
    flex: 0.8;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__image-wrapper {
    width: 70%;
    position: relative;

    img {
      width: 100%;
      height: auto;
      border-radius: 12px;
      transition: transform 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    }

    &:hover img {
      transform: scale(1.05) rotate(1deg);
    }

    @include respond-to("md") {
      width: 85%;
    }

    @include respond-to("xl") {
      width: 80%;
    }
  }
}

/* ─── CTA Section ─── */
.projects-cta {
  margin: 40px 15px;
  padding: 40px 25px;
  background: $text-color;
  color: $background-color;
  border-radius: 20px;
  text-align: center;
  position: relative;
  overflow: hidden;

  &::before {
    content: "";
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(
      circle at 30% 30%,
      rgba($brand-color-1, 0.08) 0%,
      transparent 60%
    );
    pointer-events: none;
  }

  @include respond-to("md") {
    margin: 50px 25px;
    padding: 60px 40px;
  }

  @include respond-to("xl") {
    margin: 60px 100px;
    padding: 80px 60px;
  }

  &__inner {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    max-width: 650px;
    margin: 0 auto;

    h2 {
      font-size: 28px;
      line-height: 1.2;

      @include respond-to("md") {
        font-size: 36px;
      }
    }

    p {
      font-size: 15px;
      line-height: 1.7;
      opacity: 0.8;

      @include respond-to("md") {
        font-size: 16px;
      }
    }
  }

  &__buttons {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 12px;
    margin-top: 8px;

    :deep(.button) {
      background: $brand-color-1;
      color: $primary-color;

      .button__icon-wrapper {
        background: $primary-color;
        color: $brand-color-1;
      }

      &:hover {
        background: $primary-color;
        color: $text-color;

        .button__icon-wrapper {
          background: $text-color;
          color: $primary-color;
        }
      }
    }
  }
}
</style>