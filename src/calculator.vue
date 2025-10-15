<script setup>
import { ref, onMounted } from 'vue'

const myInput1 = ref(0)
const myInput2 = ref(0)
// const plus = ref('+')
// const minus = ref('-')
// const divide = ref('/')
// const times = ref('*')
const answer = ref('')

const add = () => {
  answer.value = myInput1.value + myInput2.value
}
const sub = () => {
  answer.value = myInput1.value - myInput2.value
}
const div = () => {
  answer.value = myInput1.value / myInput2.value
}
const mul = () => {
  answer.value = myInput1.value * myInput2.value
}
</script>
<template>
  <input type="number" :class="num1" v-model="myInput1" />
  <br />
  <input type="number" :class="num2" v-model="myInput2" />
  <br />
  <input type="button" value="+" @click="add" />
  <input type="button" value="-" @click="sub" />
  <input type="button" value="/" @click="div" />
  <input type="button" value="*" @click="mul" />
  <h2>
    Answer: <span>{{ answer }}</span>
  </h2>
</template>
