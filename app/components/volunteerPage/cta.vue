<template>
  <div class="volunteerCta">
    <div class="cta-inner">
      <div class="decorative-circles">
        <div class="circle circle-1"></div>
        <div class="circle circle-2"></div>
        <div class="circle circle-3"></div>
      </div>

      <div class="content">
        <h2>Ready to Make a Difference?</h2>
        <p>
          Join hundreds of passionate young people who are already transforming communities through PVYF.
          Whether you can contribute a few hours a week or commit to a full programme cycle, your effort matters.
        </p>

        <div class="cta-actions">
          <a
            href="https://docs.google.com/forms/d/e/1FAIpQLSeY2ha51boYnvgzujvUZYU8w0NhJhICQ3lt9MPkmTB1ME7VCQ/viewform"
            target="_blank"
            rel="noopener"
            class="register-btn"
          >
            <span class="btn-icon">
              <i class="bi-pencil-square"></i>
            </span>
            Register as a Volunteer
            <span class="btn-arrow">
              <i class="bi-arrow-right"></i>
            </span>
          </a>

          <div class="secondary-links">
            <a href="/PVYF Volunteer Handbook-1.pdf" target="_blank" class="link-item">
              <i class="bi-file-earmark-pdf"></i>
              <span>Download Volunteer Handbook</span>
            </a>
            <NuxtLink to="/contact" class="link-item">
              <i class="bi-chat-dots"></i>
              <span>Contact Volunteer Coordinator</span>
            </NuxtLink>
          </div>
        </div>

        <div class="trust-badges">
          <div class="badge-item">
            <i class="bi-shield-check"></i>
            <span>Verified NGO</span>
          </div>
          <div class="badge-item">
            <i class="bi-clock-history"></i>
            <span>Flexible Hours</span>
          </div>
          <div class="badge-item">
            <i class="bi-patch-check"></i>
            <span>Certificate Awarded</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.volunteerCta {
  padding: 15px;

  @include respond-to("md") {
    padding: 25px 50px;
  }

  @include respond-to("xl") {
    padding: 30px 100px;
  }

  .cta-inner {
    position: relative;
    padding: 40px 24px;
    background: linear-gradient(135deg, $brand-color-1 0%, darken($brand-color-1, 12%) 60%, $brand-color-2 100%);
    border-radius: 20px;
    overflow: hidden;
    color: white;

    @include respond-to("md") {
      padding: 60px 50px;
    }

    @include respond-to("xl") {
      padding: 70px 80px;
    }

    .decorative-circles {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;

      .circle {
        position: absolute;
        border-radius: 50%;
        border: 1px solid rgba(white, 0.08);

        &.circle-1 {
          width: 300px;
          height: 300px;
          top: -120px;
          right: -80px;
          background: rgba(white, 0.03);
        }

        &.circle-2 {
          width: 200px;
          height: 200px;
          bottom: -60px;
          left: -40px;
          background: rgba(white, 0.02);
        }

        &.circle-3 {
          width: 120px;
          height: 120px;
          top: 50%;
          right: 15%;
          transform: translateY(-50%);
          background: rgba(white, 0.03);
        }
      }
    }

    .content {
      position: relative;
      z-index: 1;
      max-width: 700px;

      h2 {
        font-size: 28px;
        line-height: 1.15;
        margin-bottom: 16px;

        @include respond-to("md") {
          font-size: 38px;
        }

        @include respond-to("xl") {
          font-size: 44px;
        }
      }

      > p {
        font-size: 15px;
        line-height: 1.7;
        opacity: 0.9;
        margin-bottom: 32px;
        max-width: 600px;

        @include respond-to("md") {
          font-size: 16px;
        }
      }

      .cta-actions {
        display: flex;
        flex-direction: column;
        gap: 24px;
        margin-bottom: 36px;

        .register-btn {
          display: inline-flex;
          align-items: center;
          gap: 12px;
          padding: 14px 28px;
          background: white;
          color: $brand-color-1;
          border-radius: 14px;
          font-family: $alternate-font;
          font-size: 15px;
          font-weight: 700;
          letter-spacing: 0.3px;
          width: fit-content;
          transition: transform 0.3s ease, box-shadow 0.3s ease;

          .btn-icon {
            display: flex;
            align-items: center;

            i {
              font-size: 18px;
            }
          }

          .btn-arrow {
            display: flex;
            align-items: center;
            transition: transform 0.3s ease;

            i {
              font-size: 16px;
            }
          }

          &:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);

            .btn-arrow {
              transform: translateX(4px);
            }
          }
        }

        .secondary-links {
          display: flex;
          flex-direction: column;
          gap: 12px;

          @include respond-to("md") {
            flex-direction: row;
            gap: 24px;
          }

          .link-item {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            font-family: $alternate-font;
            font-size: 13px;
            opacity: 0.85;
            transition: opacity 0.3s ease, transform 0.3s ease;
            color: white;

            i {
              font-size: 16px;
            }

            &:hover {
              opacity: 1;
              transform: translateX(3px);
            }
          }
        }
      }

      .trust-badges {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
        padding-top: 24px;
        border-top: 1px solid rgba(white, 0.12);

        .badge-item {
          display: flex;
          align-items: center;
          gap: 6px;
          padding: 6px 14px;
          background: rgba(white, 0.08);
          border-radius: 20px;
          backdrop-filter: blur(4px);

          i {
            font-size: 14px;
            color: $brand-color-3;
          }

          span {
            font-family: $alternate-font;
            font-size: 11px;
            letter-spacing: 0.3px;
            opacity: 0.9;
          }
        }
      }
    }
  }
}
</style>
