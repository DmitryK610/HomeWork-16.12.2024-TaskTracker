<template>
<div>
    <h1>Трекер задач</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Введите новую задачу"/>
    <ul>
        <li v-for="(task, index) in tasks" :key="index">{{ task }}
            <button @click="deleteTask(index)">Удалить</button>
        </li>
    </ul>
</div>

</template>
<script lang="ts">
import { defineComponent } from 'vue';
import { RouterLink } from 'vue-router';
export default defineComponent(
    {
        name: 'ToDoList',
        data() {
         return {
            newTask:'',
            tasks: [] as string[]
         };
        },
        methods: {
            addTask(){
                if (this.newTask.trim()){
                    this.tasks.push(this.newTask);
                    this.newTask = '';
                }
            },
            deleteTask(index) {
      this.tasks.splice(index, 1);
    }
        },
    }
);
</script>