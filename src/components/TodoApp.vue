<template>
    <div class="Contain">
        <input v-model="todoText" @keyup.enter="addTask" placeholder="enter the task">
        <button @click="addTask">Add Task</button>
        <ul>
            <li v-for="todo in todolist" :key="todo.id" :class="{done: todo.done}">{{ todo.text }}
                <button @click="todo.done = !todo.done">✔</button>
                <button @click="removeTask(todo)">❌</button>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from 'vue';


let id = 0;

const todolist = ref([{
    id: id++,
    text: 'cum',
    done: false,
}]);
const todoText = ref('')


const addTask = () => {
    todolist.value.push({
        id: id++,
        text: todoText.value,
        done: false,
    });
    todoText.value = '';

}



function removeTask(todo) {
    todolist.value = todolist.value.filter((t) => t !== todo);
}




</script>


<style>
.done {
    text-decoration: line-through;
}
</style>