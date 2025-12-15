<script setup>
import { ref } from 'vue'

const title = ref('Learning Project')
const count = ref(0)

const increment = () => {
    count.value++ // refの値を変えるときは .value が必要
}
</script>

<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <p>簡単なページを作成しました。</p>
    <p>カウント: {{ count }}</p>
    <button @click="increment">カウントアップ</button>
    <p>
    <input type="text" v-model="title">
    </p>

  </div>
</template>

<style scoped>
.container {
  font-family: sans-serif;
  text-align: center;
  margin-top: 50px;
}
</style>
