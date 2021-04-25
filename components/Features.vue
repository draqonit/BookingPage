<template>
  <section class="bg-white border-b py-10 mt-20">
    <div class="container max-w-5xl mx-auto m-8">
      <h1
        class="w-full my-2 text-5xl font-bold leading-tight text-center text-gray-800"
      >
        Features
      </h1>
      <div class="w-full mb-4">
        <div
          class="h-1 mx-auto gradient w-64 opacity-25 my-0 py-0 rounded-t"
        ></div>
      </div>
      <feature-right
        headline="Online Bookings"
        content="Your booking is now online, skip the waiting, and share the joy. Booking online is fast and rewarding."
      >
        <img src="~assets/img/badminton1.png" alt slot="svg" />
      </feature-right>
      <feature-left
        headline="Safe and Secure"
        content="Book instantly at the same rate, no additional cost. Instant payment and 100% secure!"
      >
        <img src="~assets/img/connected-world.svg?inline" alt slot="svg" />
      </feature-left>
    </div>
  </section>
</template>

<script>
import FeatureRight from '@/components/FeatureRight'
import FeatureLeft from '@/components/FeatureLeft'

export default {
  name: 'Features',
  components: {
    'feature-right': FeatureRight,
    'feature-left': FeatureLeft
  }
}
</script>
