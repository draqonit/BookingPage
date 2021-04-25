<template>
  <div class="flex justify-center w-screen h-screen">

      <div class="p-2 h-screen flex justify-center items-center text-gray-600 bg-blue-200">



        <div
      class="bg-white p-4 rounded-md w-full"
      style="box-shadow: 0 0 6px 2px rgba(0, 0, 0, 0.25)"
    >
      <h2 class="font-bold text-xl mb-4">Enter Booking Information</h2>


          <div class="booking space-y-3">
        <select v-model="court">
          <option value="court_01">Badminton Court 1</option>
          <option value="court_02">Badminton Court 2</option>
        </select>

 
        <div class="w-full">
          <span class="mb-1 text-sm">Select Date and Time</span>
          <date-pick
            v-model="date"
            class="w-full border px-4 py-2 text-base"
            :pick-time="true"
            :use12-hour-clock="true"
            :format="'YYYY-MM-DD HH:mm'"
            :display-format="'YYYY.MM.DD H:mm A'"
          ></date-pick>
        </div>
        <span class="pt-4 text-sm">Select How many Hours</span><br>
        <input v-model="hours" type="number" placeholder="How many hours" />
        <p>Per hour rate is RM50</p>

        <p class="font-bold">Total: RM {{ Number(hours) * 50 }}</p>
      </div>

      <div>
        <button
          class="w-full bg-indigo-700 text-white py-2 rounded-md font-bold mt-4 hover:bg-indigo-500 transition duration-150 ease-in focus:outline-none"
          @click="handleBooking"
        >
          Confirm Booking
        </button>
      </div>

</div>
      </div>


  </div>

</template>

<script>
import 'vue-date-pick/dist/vueDatePick.css'
const DatePick = require('vue-date-pick')

export default {
  components: { DatePick },
  layout: "topbar",

  data() {
    return {
      date: '',
      court: '',
      hours: 0,
    }
  },

  methods: {
    handleBooking() {
  

      if (!this.date || !this.court || !this.hours) {
        alert('Please fill all the informations')
      } else {

        const date = new Date(this.date)
        if (date < new Date()) {
          alert('Please select a date and time later than today')
        } else {
      
          this.$router.push({
            path: '../booking/Payment',
            query: { total: Number(this.hours) * 100 },
          })
        }
      }
    },
  },
}

</script>

<style scoped>
.booking input,
.booking select {
  @apply border 

}

.booking input:focus,
.booking select:focus {
  @apply outline-none;
}

.vdpComponent >>> input {
  @apply text-base;
  width: 100% !important;
}
</style>

