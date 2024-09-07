<script setup>
import { ref } from 'vue';

/**
  todo item
  {
    text: string
    done : boolean(true/false)
  }

  key : text, done
  item.text or item['text']
**/

const inputValue = ref('');
const todoList = ref([
  { text: 'vue', done: false },
  { text: 'react', done: false },
  { text: 'vercel', done: false },
]);

const handleClickButton = () => {
  todoList.value.push({ text: inputValue.value, done: false });
};

const handleClickDeleteButton = (index) => {
  todoList.value.splice(index, 1);
};

const handleChange = (event) => {
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};
</script>
<!-- js -->

<template>
  <p>{{ todoList }}</p>
  <h1>TODO LIST</h1>

  <input v-model="inputValue" />
  <!-- <input v-model="inputValue" @change="handleChange" /> -->

  <button @click="handleClickButton">확인</button>

  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{ 'done-item': item.done }">{{ item.text }}</span>

    <div>
      <!-- <button>수정</button> -->
      <button @click="handleClickDeleteButton(index)">삭제</button>
    </div>
  </div>
</template>
<!-- html -->

<style scoped>
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1p solid gray;
}

.done-item {
  text-decoration: line-through;
}
</style>
<!-- css -->
