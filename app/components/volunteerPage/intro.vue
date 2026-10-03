<template>
  <div class="volunteerIntro">
    <div class="hero-image">
      <img src="/images/volunteers/overview.jpg" alt="PVYF Volunteers working together in the community" />
      <div class="hero-overlay">
        <p class="tagline">Join a Movement. Make a Difference.</p>
      </div>
    </div>

    <div class="intro-text">
      <div class="intro-label">
        <i class="bi-asterisk"></i>
        <p>Volunteer With Us</p>
      </div>
      <h2>Be Part of Something Greater</h2>
      <p>
        Volunteering with the Princess Vanessa Yemilo Foundation is more than giving your time — it's
        an opportunity to grow, connect, lead, and create real impact. Whether you're passionate about
        youth empowerment, environmental sustainability, media, or community outreach, PVYF has a place
        for you. Our volunteers are the heartbeat of everything we do, from school outreach programmes
        to national-scale events like <strong>Work It Out</strong> and the <strong>WAKE UP School Outreach</strong>.
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.volunteerIntro {
  max-width: 1200px;
  margin: 0 auto;
  padding: 25px 15px;

  @include respond-to("md") {
    padding: 35px 50px;
  }

  @include respond-to("xl") {
    padding: 35px 100px;
  }

  .hero-image {
    position: relative;
    width: 100%;
    height: 260px;
    border-radius: 16px;
    overflow: hidden;
    margin-bottom: 30px;

    @include respond-to("md") {
      height: 360px;
    }

    @include respond-to("xl") {
      height: 420px;
    }

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
    }

    .hero-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      padding: 30px 20px 20px;
      background: linear-gradient(transparent, rgba($secondary-color, 0.85));

      .tagline {
        color: white;
        font-family: $alternate-font;
        font-size: 18px;
        font-weight: 700;
        letter-spacing: 0.5px;

        @include respond-to("md") {
          font-size: 24px;
        }
      }
    }
  }

  .intro-text {
    .intro-label {
      display: flex;
      align-items: baseline;
      gap: 10px;
      margin-bottom: 10px;
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
      margin-bottom: 16px;
      line-height: 1.2;

      @include respond-to("md") {
        font-size: 32px;
      }

      @include respond-to("xl") {
        font-size: 38px;
      }
    }

    > p {
      line-height: 1.75;
      font-size: 16px;
      max-width: 900px;

      strong {
        color: $brand-color-1;
      }
    }
  }
}
</style>
