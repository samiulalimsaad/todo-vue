<template>
    <div class="overflow-x-auto w-1/2">
        <table class="table w-full">
            <thead>
                <tr>
                    <th></th>
                    <th>Title</th>
                    <th>Description</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(todo, i) in todos" :key="todo.id">
                    <th>{{ i + 1 }}</th>
                    <td>{{ todo.title }}</td>
                    <td>{{ todo.descripton }}</td>
                    <td class="flex gap-2">
                        <button class="btn btn-warning">Edit</button>
                        <button class="btn btn-error">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

const todos = ref([]);
onMounted(
    () => (todos.value = JSON.parse(localStorage.getItem("todo-vue")) || [])
);
</script>
