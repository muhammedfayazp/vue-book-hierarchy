<script setup>
import { ref } from "vue";
import BookForm from "./BookForm.vue";
import BookList from "./BookList.vue";

const books = ref({
  A: [
    { title: "abc", authorFirst: "ram", authorLast: "dev", year: "1993" }
  ],
  B: [
    { title: "rret", authorFirst: "mohammed", authorLast: "fayis", year: "1996" },
    { title: "dfg", authorFirst: "akber", authorLast: "khan", year: "2000" }
  ]
});

const addBook = (book) => {
  const group = book.title[0].toUpperCase();
  if (!books.value[group]) books.value[group] = [];
  books.value[group].push(book);
};
</script>

<template>
  <div>
    <BookForm @add-book="addBook" />
    <hr />
    <BookList :books="books" />
  </div>
</template>
