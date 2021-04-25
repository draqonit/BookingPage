<template>
  <div
    class="bg-gray-200 p-2 h-screen flex justify-center items-center text-gray-600"
  >
    <!-- Show this div when page loads -->
    <div
      v-if="!message"
      class="bg-white p-4 rounded-md w-full"
      style="box-shadow: 0 0 6px 2px rgba(0, 0, 0, 0.25)"
    >
      <h2 class="text-xl font-bold mb-4">Payment</h2>

      <p class="font-semibold mb-2">Total: US${{ total }}</p>

      <form id="payment-form">
        <div id="card-element" class="border py-3 px-2">
          <!-- Stripe Elements will create input elements here -->
        </div>

        <!-- Stripe put the error messages in this element -->
        <div
          id="card-errors"
          role="alert"
          class="text-xs text-red-600 mt-1"
        ></div>

        <button
          id="submit"
          class="w-full bg-indigo-700 text-white py-2 rounded-md font-bold mt-4 hover:bg-indigo-500 transition duration-150 ease-in focus:outline-none"
          @click="handlePayment"
        >
          Submit Payment
        </button>
      </form>
    </div>

    <!-- Show this div afterpayment is sccussful -->
    <div
      v-else
      class="bg-white p-4 rounded-md w-full font-bold"
      style="box-shadow: 0 0 6px 2px rgba(0, 0, 0, 0.25)"
    >
      {{ message }}
      <nuxt-link to="/" class="block mt-4 underline text-indigo-700"
        >Back To Home</nuxt-link
      >
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
    }
  },

  computed: {
    total() {
      // get the total price from url query here
      return this.$route.query.total
    },
  },

  mounted() {
    // Init stripe when page is mounted
    // See this link for more info https://stripe.com/docs/payments/accept-a-payment?ui=elements
    // eslint-disable-next-line no-undef
    const stripe = Stripe('pk_test_TYooMQauvdEDq54NiTphI7jx')

    // Set up Stripe.js and Elements to use in checkout form
    const elements = stripe.elements()
    const style = {
      base: {
        color: '#32325d',
      },
    }

    const card = elements.create('card', { style })
    card.mount('#card-element')

    // Handle stripe errors
    card.on('change', ({ error }) => {
      const displayError = document.getElementById('card-errors')
      if (error) {
        displayError.textContent = error.message
      } else {
        displayError.textContent = ''
      }
    })
  },

  methods: {
    handlePayment() {
      // Fake payment response
      this.message = 'Thanks for your booking and payment'
    },
  },
}
</script>

<style></style>
