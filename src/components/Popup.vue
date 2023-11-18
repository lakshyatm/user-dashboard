<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="popup">
    <div class="popup-content">
      <button @click="generateReport">Generate Report</button>
      <!-- Display user details here -->
      <div>{{ user.username }}</div>
      <div>{{ user.email }}</div>
      <div>{{ user.phone }}</div>
      <div>{{ user.id }}</div>
      <div>{{ user.creationDate }}</div>
      <button @click="$emit('close')">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  methods: {
    generateReport() {
      // Implement report generation logic here
      console.log('Generating report for user:', this.user.username);
    },
  },
};
</script>

<style scoped>
.popup {
  /* Styling for the overlay background */
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup-content {
  /* Styling for the popup content */
  background: #fff;
  padding: 20px;
  border-radius: 8px;
}
</style>
