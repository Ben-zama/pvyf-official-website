<template>
  <div class="impactSection">
    <div class="heading">
      <div class="intro">
        <i class="bi-asterisk"></i>
        <p>Impact Overview</p>
      </div>
      <h2>Driving Sustainable Change</h2>
      <p>
        Empowering youths to transform purpose into actionable community
        solutions.
      </p>
    </div>

    <div class="container">
      <div v-for="item in impact" :key="item" class="card">
        <div class="icon">
          <i :class="item.icon"></i>
        </div>
        <div class="text">
          <div class="stat">
            <h3>{{ item.stat }}</h3>
            <span>+</span>
          </div>
          <h4>{{ item.title }}</h4>
          <p>{{ item.info }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const impact = [
  {
    icon: "bi-mortarboard-fill",
    stat: "400",
    title: "Students Reached",
    info: "Engaged in purpose discovery, leadership, and SDG awareness through the WAKE UP School Outreach Program.",
  },
  {
    icon: "bi-people-fill",
    stat: "130",
    title: "Youths Trained",
    info: "Equipped with practical vocational skills, eco-craft techniques, and digital storytelling during the Work It Out Training Program.",
  },
  {
    icon: "bi-person-arms-up",
    stat: "120",
    title: "Pilot Participants",
    info: "Successfully reached through early initiatives addressing environmental sensitization and self-discovery.",
  },
  {
    icon: "bi-person-vcard-fill",
    stat: "60",
    title: "Community Volunteers",
    info: "Mobilized for hands-on climate action during the Mahuta Community Cleanup.",
  },
];
</script>

<style lang="scss">
.impactSection {
  margin-top: 50px;
  padding: 25px 15px;
  background: $primary-color;
  color: $background-color;

  @include respond-to("md") {
    padding: 50px;
  }

  @include respond-to("xl") {
    padding: 50px 100px;
  }

  .heading {
    .intro {
      display: flex;
      align-items: baseline;
      gap: 10px;
      i {
        color: color-mix(in srgb, $brand-color-1 75%, #FF00FF);
      }
      p {
        font-family: $alternate-font;
        font-size: 18px;
      }
    }
    h2 {
      margin: 10px 0;
    }

    @include respond-to("md") {
      max-width: 700px;
      h2 {
        font-size: 30px;
      }
    }
  }

  .container {
    margin-top: 25px;
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 15px;

    @include respond-to("md") {
      grid-template-columns: repeat(2, 1fr);
    }

    @include respond-to("xl") {
      grid-template-columns: repeat(4, 1fr);
    }

    .card {
      position: relative;
      padding: 15px;
      background: $background-color;
      color: $text-color;
      border-radius: 16px;
      .icon {
        position: absolute;
        width: 48px;
        height: 48px;
        top: 0;
        right: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        background: $brand-color-1;
        border-radius: 50%;
        outline: 6px solid $primary-color;
        i {
          height: 24px;
          color: $background-color;
          font-size: 24px;
        }
      }

      .text {
        display: flex;
        flex-direction: column;
        gap: 5px;
        .stat {
          display: flex;
          align-items: baseline;
          gap: 5px;
          h3 {
            font-size: 32px;
          }
          span {
            color: $brand-color-1;
            font-size: 32px;
            font-weight: bold;
          }
        }
        p {
          font-size: 14px;
        }
      }
    }
  }
}
</style>