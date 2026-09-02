<script setup>
defineEmits(["close-menu"]);
</script>

<template>
  <div class="navigation">
    <NuxtLink to="/" @click="$emit('close-menu')">Home</NuxtLink>
    <NuxtLink to="/about" @click="$emit('close-menu')">Who We Are</NuxtLink>
    <NuxtLink to="/projects" @click="$emit('close-menu')"
      >Our Projects</NuxtLink
    >
    <NuxtLink to="/volunteer" @click="$emit('close-menu')"
      >Get Involved</NuxtLink
    >
    <NuxtLink to="/contact" @click="$emit('close-menu')">Contact Us</NuxtLink>
  </div>

  <div class="info">
    <div class="logo">
      <img src="/images/full.png" alt="" />
    </div>

    <div class="about">
      <div class="section-label"><h3>About Us</h3></div>
      <p>
        The Princess Vanessa Yemilo Foundation (PVYF) is a youth-focused,
        community-driven non-governmental organisation committed to raising a
        generation of purpose-driven, skilled, socially responsible, and
        environmentally conscious young people equipped to create meaningful and
        sustainable change within their communities.
        <a href="/about">read more</a>
      </p>
    </div>

    <div class="contact">
      <div class="section-label"><h3>Get in Touch</h3></div>
      <div class="contact-blocks">
        <div class="contact-block">
          <div class="block-header">
            <i class="bi-telephone-fill"></i>
            <h4>Call on</h4>
          </div>
          <div class="block-links">
            <a href="tel:+2349129311253">+2349129311253</a>
            <a href="tel:+2349031974048">+2349031974048</a>
          </div>
        </div>
        <div class="contact-block">
          <div class="block-header">
            <i class="bi-envelope-fill"></i>
            <h4>Email</h4>
          </div>
          <div class="block-links">
            <a href="mailto:pvyfoundation.contact@gmail.com"
              >pvyfoundation.contact@gmail.com</a
            >
            <a href="mailto:pvyfoundation.partnership@gmail.com"
              >pvyfoundation.partnership@gmail.com</a
            >
            <a href="mailto:pvyfoundation.media@gmail.com"
              >pvyfoundation.media@gmail.com</a
            >
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="socials">
    <a href=""><i class="bi-instagram"></i></a>
    <a href=""><i class="bi-twitter-x"></i></a>
    <a href=""><i class="bi-linkedin"></i></a>
    <a href=""><i class="bi-facebook"></i></a>
  </div>
</template>

<style lang="scss" scoped>
.navigation {
  height: 90%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 30px;
  font-family: $alternate-font;
  font-size: 30px;
  text-align: center;
  a {
    transition: 0.3s;
    &:hover {
      transform: scale(1.1);
      color: $brand-color-1;
    }
  }

  @include respond-to("md") {
    font-size: 48px;
  }

  @include respond-to("xl") {
    display: none;
  }
}

.info {
  margin-top: 50px;
  display: none;
  flex-direction: column;
  gap: 32px;
  padding: 8px 0;
  width: 100%;

  .logo {
    width: 65%;
    height: auto;
    img {
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
  }

  // Shared section header style
  .section-label {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 12px;

    h3 {
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      opacity: 0.5;
      white-space: nowrap;
    }

    &::after {
      content: "";
      flex: 1;
      height: 1px;
      background: $text-color;
      opacity: 0.25;
    }
  }

  .about {
    display: flex;
    flex-direction: column;

    p {
      font-size: 13px;
      line-height: 1.75;
      color: $text-color;
      opacity: 0.7;

      a {
        display: inline-flex;
        align-items: center;
        gap: 4px;
        color: $brand-color-1;
        font-weight: 600;
        font-size: 12px;
        text-decoration: none;
        opacity: 1;
        transition: gap 0.25s ease;

        &::after {
          content: "→";
          transition: transform 0.25s ease;
        }

        &:hover {
          gap: 8px;
          &::after {
            transform: translateX(3px);
          }
        }
      }
    }
  }

  .contact {
    display: flex;
    flex-direction: column;

    .contact-blocks {
      display: flex;
      flex-direction: column;
      gap: 18px;
    }

    .contact-block {
      display: flex;
      flex-direction: column;
      gap: 6px;

      .block-header {
        display: flex;
        align-items: center;
        gap: 8px;

        i {
          font-size: 13px;
          color: $brand-color-1;
          flex-shrink: 0;
        }

        h4 {
          font-family: $alternate-font;
          font-size: 11px;
          letter-spacing: 0.08em;
          opacity: 0.75;
        }
      }

      .block-links {
        display: flex;
        flex-direction: column;
        gap: 4px;
        padding-left: 21px;

        a {
          position: relative;
          color: $text-color;
          font-size: 13px;
          font-weight: 500;
          width: max-content;
          transition: color 0.25s ease;
          opacity: 0.75;

          &::before {
            content: "";
            position: absolute;
            left: 0;
            bottom: -1px;
            width: 0;
            height: 1px;
            border-radius: 10px;
            background: $brand-color-1;
            transition: width 0.25s ease;
          }

          &:hover {
            color: $brand-color-1;
            opacity: 1;
            &::before {
              width: 100%;
            }
          }
        }
      }
    }
  }

  @include respond-to("xl") {
    display: flex;
  }
}

.socials {
  height: 10%;
  display: flex;
  align-items: center;
  gap: 24px;
  font-size: 24px;
  a {
    transition: 0.3s;
    &:hover {
      padding: 0 10px;
      transform: translateY(5px) scale(1.1);
      color: $brand-color-1;
    }
  }

  @include respond-to("md") {
    font-size: 36px;
  }

  @include respond-to("xl") {
    height: auto;
    width: 100%;
    font-size: 24px;
  }
}
</style>