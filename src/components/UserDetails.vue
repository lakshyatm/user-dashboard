<template>
  <div class="max-w-4xl mx-auto mt-8 bg-gray-200 p-8 rounded-md">
    <input v-model="searchQuery" placeholder="Search by username"
           class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline mb-6" />

    <table class="min-w-full bg-white border border-gray-300 shadow rounded-md overflow-hidden">
      <!-- Table headers -->
      <thead class="bg-blue-500 text-white">
        <tr>
          <th class="py-2 px-4 border-b">Username</th>
          <th class="py-2 px-4 border-b">Email</th>
          <th class="py-2 px-4 border-b">Phone</th>
          <th class="py-2 px-4 border-b">ID</th>
          <th class="py-2 px-4 border-b">Creation Date</th>
        </tr>
      </thead>
      <!-- Table rows -->
      <tbody>
        <tr v-for="user in filteredUsers" :key="user.id" @click="openPopup(user)"
            class="transition-all hover:bg-gray-100 cursor-pointer">
          <td class="py-2 px-4 border-b">{{ user.username }}</td>
          <td class="py-2 px-4 border-b">{{ user.email }}</td>
          <td class="py-2 px-4 border-b">{{ user.phone }}</td>
          <td class="py-2 px-4 border-b">{{ user.id }}</td>
          <td class="py-2 px-4 border-b">{{ user.creationDate }}</td>
        </tr>
      </tbody>
    </table>

    <Popup v-if="selectedUser" :user="selectedUser" @close="closePopup" />
  </div>
</template>

<script>
import Popup from './Popup.vue';

export default {
  data() {
    return {
      searchQuery: '',
      selectedUser: null,
      users: [],
    };
  },
  created() {
    this.loadUsers();
  },
  computed: {
    filteredUsers() {
      return this.users ? this.users.filter(user =>
        user.username.toLowerCase().includes(this.searchQuery.toLowerCase())
      ) : [];
    },
  },
  methods: {
    openPopup(user) {
      this.selectedUser = user;
    },
    closePopup() {
      this.selectedUser = null;
    },
    loadUsers() {
      const savedUsers = localStorage.getItem('users');
      if (savedUsers) {
        this.users = JSON.parse(savedUsers);
      }
    },
  },
  components: {
    Popup,
  },
};
</script>

<style scoped>
/* Add any additional styles specific to this component */
</style>
