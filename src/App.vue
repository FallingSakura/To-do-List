<script setup>
import { ref, reactive, watch } from 'vue';
const title = ref('To-do App');
// const str = ref('item');
// const isCheck = ref(false);

// console.log(title.value);

// function add() {
//   console.log(str.value);
//   str.value = '8888';
// }
// function check() {
//   isCheck.value = !isCheck.value;
//   if (isCheck.value) {
//     str.value = 'completed';
//   }
//   else {
//     str.value = 'item';
//   }
// }

// const list = ref(['Eat', 'Sleep', 'Play']);

const todo = ref('');
const list = ref([
  {
    isCompleted: false,
    text: 'Eat'
  },
  {
    isCompleted: false,
    text: 'Sleep'
  },
  {
    isCompleted: false,
    text: 'Play'
  }
]);

function add() {
  if (todo.value === '')
  {
    alert("Please Input.");
    return;
  }
  list.value.push({isCompleted: false, text: todo.value});
  todo.value = '';
}

function del(index) {
  list.value.splice(index, 1);
  // 从 index 开始删除 1 个
}

import Mybutton from './components/button.vue'

function hello(str) {
  console.log(str);
}

</script>
<template>
  <div>
    <div class="todo-app">
      <div v-show="true" class="title">{{ title }}</div>

      <div class="todo-form">
        <input
          v-model="todo"
          type="text"
          class="todo-input"
          placeholder="Add a todo"
        />
        <div @click="add" class="todo-button">Add Todo</div>
      </div>
      <!-- <div v-for="(i, index) in list" :key="index" :class="[isCheck? 'completed' : 'item']"> -->
        <!-- As an Array -->
      <div v-for="(item, index) in list" :key="index" :class="[item.isCompleted ? 'completed' : 'item']">
        <div>
          <input v-model="item.isCompleted" type="checkbox">
          <span class="name">{{ item.text }}</span>
        </div>
        <div @click="del(index)" class="del">del</div>
      </div>
    </div>
    <Mybutton @ok="hello" text="Hello"></Mybutton>
    <Mybutton text="HaHa"></Mybutton>
  </div>
</template>

<style scoped>
.todo-app {
  box-sizing: border-box;
  margin-top: 40px;
  margin-left: 1%;
  padding-top: 30px;
  width: 98%;
  height: 500px;
  background: #ffffff;
  border-radius: 5px;
}

.title {
  text-align: center;
  font-size: 30px;
  font-weight: 700;
}

.todo-form {
  display: flex;
  margin: 20px 0 30px 20px;
}

.todo-button {
  width: 100px;
  height: 52px;
  border-radius: 0 20px 20px 0;

  text-align: center;
  background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
  color: #fff;
  line-height: 52px;
  cursor: pointer;
  font-size: 14px;
  user-select: none;
}

.todo-input {
  padding: 0px 15px 0px 15px;
  border-radius: 20px 0 0 20px;
  border: 1px solid #dfe1e5;
  outline: none;
  width: 60%;
  height: 50px;
}

.item {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
}

.del {
  color: red;
  cursor: pointer;
  user-select: none;
}

.completed {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 80%;
  height: 50px;
  margin: 8px auto;
  padding: 16px;
  border-radius: 20px;
  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
  text-decoration: line-through;
  opacity: 0.4;
}
</style>
