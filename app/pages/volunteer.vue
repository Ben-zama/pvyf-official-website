<template>
    <div class="volunteerPage">

      <VolunteerPageIntro />

      <VolunteerPageUnits />

      <VolunteerPageBenefits />

      <VolunteerPageFeatured />

      <VolunteerPageCta />

    </div>
</template>

<script setup>
definePageMeta({
  layout: 'page-header',
  title: 'Get Involved'
});

useHead({
  title: 'Volunteer With Us | PVYF - Princess Vanessa Yemilo Foundation',
  meta: [
    {
      name: 'description',
      content: 'Join the PVYF volunteer team and make a real difference. Explore our volunteering units, discover benefits, and register to become a volunteer with the Princess Vanessa Yemilo Foundation.'
    }
  ]
});
</script>

<style lang="scss" scoped>

</style>