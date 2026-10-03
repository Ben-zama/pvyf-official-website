<template>
  <div class="team">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Meet Our Team</p>
      </div>
      <h2>The Founder & Head of Departments</h2>
    </div>

    <div class="container">
      <div v-for="item in team" :key="item.name" class="card">
        <img :src="item.img" alt="">
        <div class="box">
          <div class="text">
            <h3>{{ item.name }}</h3>
            <p>{{ item.role }}</p>
          </div>
          <div v-if="item.links?.length" class="links">
            <a v-for="link in item.links" :key="link.icon" :href="link.url" target="_blank" rel="noopener">
              <i :class="link.icon"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const team = [
  {
    name: "Princess Vanessa Emmanuel",
    img: "/images/team/vanessa.jpg",
    role: "Founder / Executive Director",
    links: [
      { icon: "bi-instagram", url: "https://www.instagram.com/princess__the_trailblazer/" },
      { icon: "bi-linkedin", url: "https://www.linkedin.com/in/princess-vanessa-emmanuel-92386a308?utm_source=share_via&utm_content=profile&utm_medium=member_ios" }
    ]
  },
  {
    name: "Ahmed Abraham Armani",
    img: "/images/team/ahmed.jpg",
    role: "Head of Operations & Administrations",
    links: [
      { icon: "bi-facebook", url: "https://www.facebook.com/share/1H9pNE3rMf/?mibextid=wwXIfr" },
    ]
  },
  {
    name: "Ojo Moses Ojonugwa",
    img: "/images/team/ojo.jpg",
    role: "Head of Media & Communications",
    links: [
      { icon: "bi-facebook", url: "https://www.facebook.com/profile.php?id=100010982868816" },
      { icon: "bi-youtube", url: "https://www.youtube.com/@EndowedCircle/featured" }
    ]
  },
  {
    name: "Dorathy Gimbiya Bodam",
    img: "/images/team/dorathy.jpg",
    role: "Head of Monitoring, Evaluation & Reporting Department",
    links: [
      { icon: "bi-facebook", url: "https://www.facebook.com/share/1RKGEjxvkL/?mibextid=wwXIfr" },
    ]
  },
  {
    name: "Bishop Friday",
    img: "/images/team/bishop.jpg",
    role: "Head of Community Engagement & Partnerships Department",
    links: [
      { icon: "bi-instagram", url: "https://www.instagram.com/friday.bishop?stkn=Mnh5MjE1djVpMjJ5" },
    ]
  },
  {
    name: "Nita Zugwai Daniel",
    img: "/images/team/anita.jpg",
    role: "Head of Training & Facilitation Department",
    links: [
      { icon: "bi-facebook", url: "https://www.facebook.com/profile.php?id=100075776135822&mibextid=wwXIfr" },
    ]
  },
];
</script>

<style lang="scss">
.team {
  background: $primary-color;
  padding: 25px 15px;

  @include respond-to("md") {
    padding: 50px;
  }

  @include respond-to("lg") {
    padding: 50px 100px;
  }

  .heading {
    margin-bottom: 15px;
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
    }

    @include respond-to("md") {
      max-width: 600px;
      margin-bottom: 25px;
      h2 {
        font-size: 32px;
      }
    }

    @include respond-to("xl") {
      margin-bottom: 50px;
      max-width: 800px;
    }
  }

  .container {
    margin: 0 auto;
    max-width: 1000px;
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 25px;

    .card {
      position: relative;
      height: 400px;
      border-radius: 16px;
      overflow: hidden;
      cursor: pointer;
      background: rgba($brand-color-1, 0.5);

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: top;
        transition: transform 0.5s ease;
      }

      .box {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 25%;
        display: flex;
        justify-content: center;
        align-items: center;
        background: linear-gradient( transparent, $secondary-color);
        transition: height 0.45s cubic-bezier(0.4, 0, 0.2, 1),
                    background 0.45s cubic-bezier(0.4, 0, 0.2, 1);

        .text {
          color: white;
          text-align: center;
          transition: opacity 0.3s ease, transform 0.3s ease;
          opacity: 1;
          transform: translateY(0);
          max-width: 80%;
          h3 {
            font-family: $alternate-font;
            font-weight: 900;
            font-size: 20px;
          }
          p {
            margin-top: 8px;
            font-family: $alternate-font;
            font-size: 12px;
          }
        }

        .links {
          position: absolute;
          display: flex;
          gap: 16px;
          opacity: 0;
          transform: translateY(12px);
          transition: opacity 0.35s ease 0.15s, transform 0.35s ease 0.15s;

          a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            background: rgba(white, 0.12);
            backdrop-filter: blur(6px);
            border: 1px solid rgba(white, 0.2);
            color: white;
            font-size: 18px;
            text-decoration: none;
            transition: background 0.25s ease, transform 0.25s ease, border-color 0.25s ease;

            &:hover {
              background: $brand-color-1;
              border-color: $brand-color-1;
              transform: scale(1.15);
            }
          }
        }
      }

      &:hover {
        img {
          transform: scale(1.08);
        }

        .box {
          height: 100%;
          background: rgba($secondary-color, 0.9);

          .text {
            opacity: 0;
            transform: translateY(-14px);
            pointer-events: none;
          }

          .links {
            opacity: 1;
            transform: translateY(0);
          }
        }
      }
    }

    @include respond-to("md") {
      grid-template-columns: repeat(2, 1fr);
    }

    @include respond-to("lg") {
      grid-template-columns: repeat(3, 1fr);
    }
  }
}
</style>