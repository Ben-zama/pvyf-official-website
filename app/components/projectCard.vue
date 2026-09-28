<template>
  <div class="card">
    <div class="text">
      <i v-if="item.icon" :class="item.icon"></i>
      <h3>{{ item.title }}</h3>
      <p>{{ item.info }}</p>
      <p v-if="item.info2" class="info2">{{ item.info2 }}</p>
      <ctaButton name="More Info" />
    </div>
    <div class="images">
      <img :src="item.img" alt="" />
    </div>
  </div>
</template>

<script setup>
defineProps({
  item: {
    type: Object,
    required: true,
  },
});
</script>

<style lang="scss" scoped>
.card {
  padding: 15px;
  display: flex;
  flex-direction: column;
  gap: 50px;
  border-radius: 16px;
  overflow: hidden;
  .text {
    display: flex;
    flex-direction: column;
    align-items: start;
    gap: 15px;
    font-size: 14px;
    h3 {
      font-size: 18px;
      font-weight: bold;
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
  .images {
    width: 75%;
    img {
      width: 100%;
      height: 100%;
      border-radius: 8px;
    }
  }

  @include respond-to("md") {
    padding: 25px;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    .text {
      width: 55%;
      h3 {
        font-size: 24px;
      }
    }
    .images {
      width: 35%;
    }
  }

  @include respond-to("xl") {
    padding: 100px 50px;
    .text {
      width: 50%;
    }
    .images {
      width: 30%;
    }
  }
}
</style>
