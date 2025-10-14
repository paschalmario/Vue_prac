<script setup>
import { ref, onMounted } from 'vue'

const name = ref('John Doe')
const status = ref('active')
const tasks = ref(['task1', 'task2', 'task3'])
const newtask = ref('hello')

const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending'
    name.value = 'Zikora'
  } else if (status.value === 'pending') {
    status.value = 'inactive'
  } else {
    status.value = 'active'
    name.value = 'John doe'
  }
}
const addtask = () => {
  if (newtask.value.trim() !== '') {
    tasks.value.push(newtask.value)
    newtask.value = ''
  }
}
const deleteTask = (index) => {
  tasks.value.splice(index, 1)
}

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos')
    const data = await response.json()
    tasks.value = data.map((task) => task.title)
  } catch (error) {
    console.log('error Fetching task')
  }
})
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <h3>Task</h3>
  <form @submit.prevent="addtask">
    <label for="newtask">Add task</label>
    <input type="text" name="newtask" id="newtask" v-model="newtask" />
    <button type="submit" @click="addtask">Submit</button>
  </form>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
        <button @click.prevent="deleteTask(index)">x</button>
      </span>
    </li>
  </ul>
  <button @click="toggleStatus">Change Status</button>
</template>
