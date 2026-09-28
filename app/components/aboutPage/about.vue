<template>
  <div class="aboutSection">
    <div class="text">
      <h2>About the Organization</h2>

      <div class="magazine-layout">
        <p>
          The Princess Vanessa Yemilo Foundation (PVYF) is a youth-focused, community-driven
          non-governmental organisation committed to raising a generation of purpose-driven, skilled,
          socially responsible, and environmentally conscious young people equipped to create
          meaningful and sustainable change within their communities.
        </p>
        <p>
          The Foundation was established in response to the growing social, economic, and
          environmental challenges affecting young people across Nigeria and Africa. These challenges
          include limited access to practical and future-focused skills, rising youth unemployment, low
          self-confidence, weak mentorship systems, inadequate leadership exposure, gender-related
          inequalities, limited civic participation, and increasing environmental issues such as poor
          waste management, pollution, and climate change.
        </p>
        <img src="/images/hero/image1.jpg" alt="">
        <p>
          PVYF believes that young people are not merely beneficiaries of development but powerful
          agents of transformation with the capacity to solve problems, drive innovation, and shape
          sustainable communities when equipped with the right knowledge, skills, mindset, and
          opportunities.
        </p>
        <p>
          Through a holistic and youth-centered approach, the Foundation empowers young people to
          discover their purpose, build leadership capacity, strengthen life skills, acquire practical
          competencies, and transform their ideas and talents into solutions that address social,
          economic, and environmental challenges.
        </p>
        <p>
          The Foundation implements its work through school outreach programmes, youth
          development initiatives, mentorship platforms, skills training programmes, environmental
          campaigns, innovation challenges, and community-based projects designed to reach young
          people at critical stages of their personal and professional development journey.
        </p>
        <img src="/images/hero/image3.jpg" alt="">
        <p>
          PVYF primarily operates through schools, communities, and grassroots structures, ensuring
          inclusive access to opportunities and creating pathways for long-term impact and community
          transformation.
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.aboutPage {
  .aboutSection {
    max-width: 1200px;
    margin: 0 auto;
    padding: 25px;

    @include respond-to("md") {
      padding: 25px 50px;
    }

    @include respond-to("xl") {
      padding: 25px 100px;
    }

    .text {
      h2 {
        font-size: 24px;
        font-family: $alternate-font;
        margin-bottom: 1.5rem;
        border-bottom: 1px solid $text-color;
        padding-bottom: 0.5rem;

        @include respond-to("md") {
          margin-top: 1rem;
          font-size: 30px;
          margin-bottom: 2rem;
        }

        @include respond-to("lg") {
          font-size: 36px;
        }
      }

      .magazine-layout {
        column-count: 1;
        column-rule: none;
        text-align: left;
        
        p {
          margin-top: 0;
          margin-bottom: 1.5rem;
          line-height: 1.7;
          font-size: 1rem;
          break-inside: avoid-column; 
          page-break-inside: avoid;
        }

        p:first-of-type::first-letter {
          float: left;
          font-size: 3.5rem;
          line-height: 0.8;
          padding-right: 0.5rem;
          padding-top: 0.2rem;
          font-weight: 700;

          @include respond-to("lg") {
            font-size: 4rem; 
          }
        }

        img {
          width: 100%;
          height: auto;
          max-height: 200px;
          margin-bottom: 1.5rem;
          object-fit: cover;
          object-position: center;
          border-radius: 16px;

          @include respond-to("md") {
            margin-bottom: 2rem;
          }
        }

        @include respond-to("md") {
          column-count: 2;
          column-gap: 2rem;
          column-rule: 1px solid #e0e0e0;
          text-align: justify;
        }

        @include respond-to("lg") {
          column-count: 3;
          column-gap: 2.5rem;
        }
      }
    }
  }
}
</style>