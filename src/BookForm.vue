<script setup>
import { ref } from "vue";

const emit = defineEmits(["add-book"]);

const newBook = ref({
  title: "",
  authorFirst: "",
  authorLast: "",
  year: ""
});

const submitForm = () => {
  if (!newBook.value.title) return;
  emit("add-book", { ...newBook.value });
  newBook.value = { title: "", authorFirst: "", authorLast: "", year: "" };
};
</script>

<template>
  <div class="form">
    <h2>Add New Book</h2>
    <form @submit.prevent="submitForm">
      <label>Title</label>
      <input v-model="newBook.title" required />

      <label>Author First</label>
      <input v-model="newBook.authorFirst" required />

      <label>Author Last</label>
      <input v-model="newBook.authorLast" required />

      <label>Year</label>
      <input v-model="newBook.year" required />

      <button type="submit">Add Book</button>
    </form>
  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  gap: 8px;
}
button { margin-top: 12px; }
</style>
