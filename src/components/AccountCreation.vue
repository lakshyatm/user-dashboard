<template>
  <div class="max-w-md mx-auto mt-8">
    <form @submit.prevent="submitForm" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label for="username" class="block text-gray-700 text-sm font-bold mb-2">Username:</label>
        <input v-model="username" id="username" type="text" required
               class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
      </div>

      <div class="mb-6">
        <label for="password" class="block text-gray-700 text-sm font-bold mb-2">Password:</label>
        <input v-model="password" id="password" type="password" required
               class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
      </div>

      <div class="flex items-center justify-between">
        <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
          Create Account
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    submitForm() {
      // Save user data to localStorage
      const userData = {
        username: this.username,
        password: this.password,
      };

      // Retrieve existing users from localStorage (if any)
      const existingUsers = JSON.parse(localStorage.getItem('users')) || [];

      // Add the new user to the list
      existingUsers.push(userData);

      // Save the updated user list back to localStorage
      localStorage.setItem('users', JSON.stringify(existingUsers));

      // Clear the form after submission
      this.username = '';
      this.password = '';

      console.log('Account created successfully');
    },
  },
};
</script>

<style scoped>
/* Add any additional styles specific to this component */
</style>
