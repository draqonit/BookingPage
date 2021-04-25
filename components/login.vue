<template>
  <div
    class="h-screen flex justify-center items-center text-gray-600"
  >
    <!-- Signin / Signup page. This is also the home page of the website -->
    <!-- We will only show either signin or signup form at a time -->

    <!-- Below div contains all the elements for signin form -->
    <div
      v-if="displayForm === 'signin'"
      class="bg-white p-4 rounded-md w-full"
      style="box-shadow: 0 0 6px 2px rgba(0, 0, 0, 0.25)"
    >
      <h2 class="text-xl font-bold mb-4">Sign In to Continue</h2>

      <!-- When we submit the form, we use .prevent modifier to prevent default action which is browser refresh -->
      <form class="form space-y-3" @submit.prevent="handleSignIn">
        <input
          v-model="signInForm.email"
          type="email"
          placeholder="Enter your Email"
        />
        <input
          v-model="signInForm.password"
          type="password"
          placeholder="Enter Your Password"
        />

        <button
          type="submit"
          class="bg-indigo-700 text-white font-bold hover:bg-indigo-500 transition duration-150 ease-in"
        >
          Sign In
        </button>
      </form>

      <p class="text-sm mt-3">
        Dont have an account?
        <!-- In this click event, we change the displayFrom value to display the signup form -->
        <button
          class="font-semibold text-indigo-700 underline"
          @click="displayForm = 'signup'"
        >
          Create an account
        </button>
      </p>
    </div>

    <!-- Below div contains all the elements for signin form -->
    <div
      v-if="displayForm === 'signup'"
      class="bg-white p-4 rounded-md"
      style="box-shadow: 0 0 6px 2px rgba(0, 0, 0, 0.25)"
    >
      <h2 class="text-xl font-bold mb-4">Sign Up for an Account</h2>

      <form class="form space-y-3" @submit.prevent="handleSignUp">
        <input v-model="signUpForm.name" type="text" placeholder="Full Name" />
        <input
          v-model="signUpForm.email"
          type="email"
          placeholder="Enter your Email"
        />
        <input
          v-model="signUpForm.phone"
          type="text"
          placeholder="Phone Number"
        />
        <input
          v-model="signUpForm.password"
          type="password"
          placeholder="Enter Your Password"
        />

        <button
          class="bg-indigo-700 text-white font-bold hover:bg-indigo-500 transition duration-150 ease-in"
        >
          Sign Up
        </button>
      </form>

      <p class="text-sm mt-3">
        Already have an account?
        <!-- In this click event, we change the displayFrom value to display the signin form -->
        <button
          class="font-semibold text-indigo-700 underline"
          @click="displayForm = 'signin'"
        >
          Sign In
        </button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      displayForm: 'signin', // default value for displayForm is "signin" so when page is loaded it will display signin form by default
      // We have bind the input fields to populate below object of signin form
      signInForm: {
        email: '',
        password: '',
      },
      // We have bind the input fields to populate below object of signup form
      signUpForm: {
        name: '',
        email: '',
        phone: '',
        password: '',
      },
    }
  },

  methods: {
    handleSignIn() {
      // We handle the signIn event here.
      // Id user did not input email or password, lets alert them. Else lets check signin data and accept or refuse signin
      if (!this.signInForm.email || !this.signInForm.password) {
        alert('Please enter email and password')
      } else if (
        this.signInForm.email === 'test@email.com' &&
        this.signInForm.password === 'Test@2020'
      ) {
        // Here the validation is sccessful, we will redirect the user to next step
        // Empty the input fields
        this.signInForm.email = ''
        this.signInForm.password = ''

        // Redirect user to booking page
        this.$router.push('/booking/page1')
      } else {
        alert('Email and/or Password are wrong')
      }
    },

    handleSignUp() {
      // Handle signup event with this method
      // First check if all input fields are filled up or not
      // If all input fields are filled up give a fake confirmations message and redirect user to signin
      if (
        !this.signUpForm.name ||
        !this.signUpForm.email ||
        !this.signUpForm.phone ||
        !this.signUpForm.password
      ) {
        alert('Please fill all the informations')
      } else {
        alert('Signed Up Successfully. Please Sign In now.')

        // Empty the input fields
        this.signUpForm.name = ''
        this.signUpForm.email = ''
        this.signUpForm.phone = ''
        this.signUpForm.password = ''

        // Display Signin form
        this.displayForm = 'signin'
      }
    },
  },
}
</script>

<style scoped>
.form input,
.form button {
  @apply border px-4 py-2 rounded-md w-full;
}

.form input:focus,
.form button:focus {
  @apply outline-none;
}
</style>
