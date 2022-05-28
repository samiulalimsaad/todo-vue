<template>
    <div class="card w-1/2 bg-base-100 shadow-xl">
        <div class="card-body">
            <h2 class="card-title justify-center my-5">Add a Todo!</h2>
            <div class="flex gap-4 flex-col">
                <div class="form-control">
                    <label class="input-group">
                        <span class="w-1/5">Title</span>
                        <input
                            type="text"
                            v-model="title"
                            placeholder="Todo Title"
                            class="input input-bordered input-success w-full"
                        />
                    </label>
                </div>
                <div class="form-control">
                    <label class="input-group">
                        <span class="w-1/5">Description</span>
                        <textarea
                            type="text"
                            v-model="descripton"
                            rows="4"
                            placeholder="Todo Descripton"
                            class="textarea textarea-success w-full"
                        ></textarea>
                    </label>
                </div>
                <div class="card-actions justify-end form-control">
                    <button @click="add" class="btn w-full btn-success">
                        Save
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const title = ref("");
const descripton = ref("");

const add = () => {
    const todo = {
        id: Date.now(),
        title: title.value,
        descripton: descripton.value,
    };
    let previousTodo = JSON.parse(localStorage.getItem("todo-vue")) || [];

    if (!previousTodo?.length) previousTodo = [];
    previousTodo.push(todo);

    localStorage.setItem("todo-vue", JSON.stringify(previousTodo));
    title.value = "";
    descripton.value = "";
};
</script>
