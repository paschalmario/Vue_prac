<script>
export default {
  data() {
    return {
      name: 'John doe',
      status: 'active',
      tasks: ['task1', 'task2', 'task3'],
      link: 'http://google.com',
    }
  },
  methods: {
    toggleStatus() {
      if (this.status === 'pending') {
        this.status = 'active'
      } else if (this.status === 'active') {
        this.status = 'pending'
      } else {
        this.status = 'Inactive'
      }
    },
  },
}
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <h3>Task</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link">link to google</a>
  <button @click="toggleStatus">Change Status</button>
</template>
