<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-100">
    <div class="flex flex-col">
      <button @click="activeTab = 'userDetails'" :class="{ 'tab-button': true, 'active-tab': activeTab === 'userDetails' }">
        User Details
      </button>
      <button @click="activeTab = 'accountCreation'" :class="{ 'tab-button': true, 'active-tab': activeTab === 'accountCreation' }">
        Account Creation
      </button>
    </div>
    <div class="ml-4">
      <div v-if="activeTab === 'userDetails'">
        <UserDetails :users="users" />
      </div>
      <div v-else-if="activeTab === 'accountCreation'">
        <AccountCreation />
      </div>
    </div>
  </div>
</template>

<script>
import UserDetails from './components/UserDetails.vue';
import AccountCreation from './components/AccountCreation.vue';

export default {
  data() {
    return {
      activeTab: 'userDetails',
      users: [
        // Placeholder user data
        { id: 1, username: 'user1', email: 'user1@example.com', phone: '123-456-7890', creationDate: '2023-01-01' },
        { id: 2, username: 'user2', email: 'user2@example.com', phone: '987-654-3210', creationDate: '2023-01-02' },
      ],
    };
  },
  components: {
    UserDetails,
    AccountCreation,
  },
};
</script>

<style scoped>
body {
  margin: 0;
}

.min-h-screen {
  min-height: 100vh;
}

.flex {
  display: flex;
}

.flex-col {
  flex-direction: column;
}

.tab-button {
  background-color: #3490dc; /* Adjust the color as needed */
  color: white;
  font-weight: bold;
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-bottom: 4px;
}

.active-tab {
  /* Styling for the active tab */
  background-color: #4a90e2; /* Adjust the color as needed */
}
</style>
