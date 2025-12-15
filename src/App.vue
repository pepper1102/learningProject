<script setup>
import { ref } from 'vue'

const title = ref('Learning Project')
const count = ref(0);
const items = ref([
  { title: '学習課題1', isDone: false },
  { title: '学習課題2', isDone: false },
  { title: '学習課題3', isDone: false }]);
const newItem = ref('');


const increment = () => {
  count.value++ // refの値を変えるときは .value が必要
}

const addItem = () => {
  if (newItem.value.trim() !== '') {
    items.value.push({
      title: newItem.value,
      isDone: false
    });
    newItem.value = '';
  }
}
const deleteItem = (index) => {
  items.value.splice(index, 1);
}
</script>


<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <p>簡単なページを作成しました。</p>
    <p>カウント: {{ count }}</p>
    <input type="text" v-model="title">
    <ul>
      <li v-for="(item, index) in items" :key="item">
        <span :class="{ done: item.isDone }" @click="item.isDone = !item.isDone">
          {{ item.title }}
        </span>
        <button @click="deleteItem(index)">削除</button>
      </li>
    </ul>
    <input type="text" v-model="newItem">
    <button @click="addItem">追加</button>
  </div>
</template>

<style scoped>
.container {
  font-family: sans-serif;
  text-align: center;
  margin-top: 50px;
}

.done {
  text-decoration: line-through;
  color: gray;
}
</style>
