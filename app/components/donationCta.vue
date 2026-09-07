<script setup>
import { ref } from 'vue'

const copied = ref(false)
const accountNumber = '1029868295'

const copyToClipboard = async () => {
  try {
    await navigator.clipboard.writeText(accountNumber)
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2000)
  } catch (err) {
    console.error('Failed to copy!', err)
  }
}
</script>

<template>
  <div class="donationCta">
    <div class="content-wrapper">
      <div class="text">
        <h2>Empower the Next Generation of Changemakers</h2>
        <p>
          Your contribution directly supports the Princess Vanessa Yemilo
          Foundation's mission to equip young people with future-ready skills,
          leadership training, and environmental sustainability education. From
          funding the WAKE UP School Outreach Program to providing materials for
          our eco-craft and vocational workshops, every donation helps transform
          youth potential into sustainable community solutions.
        </p>
        
        <div class="card">
          <img src="/images/uba.png" alt="UBA Logo">
          <h3>United Bank for Africa (UBA)</h3>
          <p class="name">Princess Vanessa Yemilo Foundation</p>
          <div class="number">
            <p>{{ accountNumber }}</p>
            <div class="copy-btn" @click="copyToClipboard" @mouseleave="copied = false">
              <i class="bi-copy"></i>
              <span class="tooltip">{{ copied ? 'Account number copied' : 'Copy account number' }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="extra-info">
        <div class="info-block">
          <h3>Other Ways to Support</h3>
          <ul>
            <li>
              <strong>Partner with Us</strong> 
              We welcome Corporate Social Responsibility (CSR) partnerships, institutional collaborations, and civil society alliances to scale our impact.
            </li>
            <li>
              <strong>In-Kind Donations</strong> 
              Support our Work It Out Training Program and Work It Out Club Series with learning materials, tools, or technical expertise.
            </li>
          </ul>
        </div>

        <div class="info-block">
          <h3>Contact for Partnerships</h3>
          <ul class="contact-list">
            <li>
              <i class="bi bi-envelope"></i>
              <a href="mailto:info@pvyfoundation.org">info@pvyfoundation.org</a>
            </li>
            <li>
              <i class="bi bi-telephone"></i>
              <div class="phones">
                <a href="tel:+2349129311253">+234 912 931 1253</a>
                <span class="divider">|</span>
                <a href="tel:+2349031974048">+234 903 197 4048</a><!--[cite: 1] -->
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.donationCta {
  margin: 15px;
  padding: 25px;
  background: $brand-color-1;
  border-radius: 16px;
  color: $background-color;

  @include respond-to("md") {
    margin: 25px 50px;
    padding: 35px;
  }

  @include respond-to("xl") {
    margin: 30px 100px;
    padding: 50px;
  }

  .content-wrapper {
    display: flex;
    flex-direction: column;
    gap: 40px;

    @include respond-to("xl") {
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      gap: 60px;
    }
  }

  .text {
    display: flex;
    flex-direction: column;
    gap: 20px;
    flex: 1.2;

    h2 {
      margin: 0;
      font-size: 28px;
      line-height: 1.2;

      @include respond-to("md") {
        font-size: 34px;
      }
    }

    > p {
      max-width: 800px;
      line-height: 1.6;
      font-size: 16px;
      opacity: 0.95;
    }

    .card {
      position: relative;
      max-width: 450px;
      padding: 20px 24px;
      display: flex;
      flex-direction: column;
      gap: 6px;
      background: #D61B0C;
      color: white;
      border-radius: 12px;
      margin-top: 10px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);

      img {
        position: absolute;
        top: 20px;
        right: 20px;
        width: 56px;
        height: auto;
        border-radius: 4px;
      }
      
      h3 {
        margin-top: 50px;
        font-weight: 500;
        font-size: 16px;
        opacity: 0.9;
      }
      
      .name {
        font-size: 18px;
        font-weight: 600;
      }
      
      .number {
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-family: $alternate-font;
        font-size: 24px;
        font-weight: bold;
        margin-top: 8px;

        .copy-btn {
          position: relative;
          display: inline-flex;
          align-items: center;
          justify-content: center;
          cursor: pointer;
          
          i {
            font-size: 22px;
            opacity: 0.8;
            transition: opacity 0.2s ease, transform 0.2s ease;
          }

          &:hover i {
            opacity: 1;
            transform: scale(1.1);
          }

          .tooltip {
            visibility: hidden;
            background-color: $background-color;
            color: $brand-color-1;
            text-align: center;
            border-radius: 6px;
            padding: 6px 10px;
            position: absolute;
            z-index: 10;
            bottom: 130%; 
            left: 50%;
            transform: translateX(-50%);
            opacity: 0;
            transition: opacity 0.3s;
            font-size: 13px;
            font-family: sans-serif;
            font-weight: normal;
            white-space: nowrap;
            pointer-events: none;
            
            &::after {
              content: "";
              position: absolute;
              top: 100%;
              left: 50%;
              margin-left: -5px;
              border-width: 5px;
              border-style: solid;
              border-color: rgba(0, 0, 0, 0.85) transparent transparent transparent;
            }
          }

          &:hover .tooltip {
            visibility: visible;
            opacity: 1;
          }
        }
      }

      @include respond-to("md") {
        h3 {
          margin-top: 25px;
        }      
        .number {
          justify-content: start;
          gap: 50px;
        }
      }
    }
  }

  .extra-info {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 35px;

    .info-block {
      h3 {
        font-size: 20px;
        margin-bottom: 16px;
        padding-bottom: 8px;
        border-bottom: 1px solid rgba($background-color, 0.2);
        font-weight: 600;
      }

      ul {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
        gap: 16px;

        li {
          font-size: 15px;
          line-height: 1.6;
          opacity: 0.9;

          strong {
            display: block;
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 4px;
            color: $background-color;
            opacity: 1;
          }
        }
      }

      .contact-list {
        gap: 12px;

        li {
          display: flex;
          align-items: center;
          gap: 12px;
          font-size: 16px;
          opacity: 1;

          i {
            font-size: 20px;
            color: $background-color;
          }

          a {
            color: $background-color;
            text-decoration: none;
            transition: opacity 0.2s ease;

            &:hover {
              opacity: 0.7;
              text-decoration: underline;
            }
          }

          .phones {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-wrap: wrap;

            .divider {
              opacity: 0.5;
            }
          }
        }
      }
    }
  }
}
</style>