<script setup>
import { ref } from "vue";

const showModal = ref(false);
const newNote = ref(""); // Typing here will display placeholder text in the note
const errorMessage = ref("");
const notes = ref([]);

const getRandomColor = () => {
  return `hsl(${Math.random() * 360}, 100%, 85%)`;
};

const addNote = () => {
  if (newNote.value.length < 10) {
    return (errorMessage.value =
      "Please write at least 10 characters in your note");
  }
  notes.value.push({
    id: Math.floor(Math.random() * 1000000),
    text: newNote.value,
    date: new Date(),
    backgroundColor: getRandomColor(),
  });
  showModal.value = false;
  newNote.value = "";
  errorMessage.value = "";
};
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <!-- could use v-show to add/remove display: none (better for SEO and screen readers cos the element is hidden not removed)-->
      <div class="modal">
        <textarea
          v-model.trim="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <p v-if="errorMessage">{{ errorMessage }}</p>
        <button @click="addNote">Add Note</button>
        <button class="close" @click="showModal = false">Close</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div
          v-for="note in notes"
          :key="note.id"
          class="card"
          :style="{ background: note.backgroundColor }"
        >
          <p class="main-text">
            {{ note.text }}
          </p>
          <p class="date">{{ note.date.toLocaleDateString("en-UK") }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}

.overlay {
  position: absolute;
  width: 100%; /* 100% of 100vw from main */
  height: 100%; /* 100% of 100vh from main */
  background: rgba(0, 0, 0, 0.77);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 750px;
  background: white;
  border-radius: 0.625em; /* 10px */
  padding: 1.875em; /* 30px */
  position: relative;
  display: flex;
  flex-direction: column;
}

textarea {
  /* border: none; */
  width: 100%;
}

.modal button {
  padding: 0.625em 1.25em; /* 10px 20px */
  font-size: 1.25rem; /* 20px */
  width: 100%;
  margin-top: 0.625em; /* 10px */
  background: blueviolet;
  border: none;
  color: white;
  cursor: pointer;
}

.modal .close {
  background: rgba(193, 15, 15);
}

.modal p {
  color: rgba(193, 15, 15);
}

.container {
  max-width: 1000px;
  padding: 0.625em; /* 10px */
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

h1 {
  font-weight: bold;
  margin-bottom: 1.5em; /* 24px */
  font-size: 4.5rem; /* 72px */
}

header button {
  border: none;
  padding: 0.625em; /* 10px */
  width: 2.5em; /* 40px */
  height: 2.5em; /* 40px */
  cursor: pointer;
  background: rgba(21, 20, 20);
  border-radius: 100%;
  color: white;
  font-size: 1.25rem; /* 20px */
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
}

.card {
  width: 14em; /* 224px */
  height: 14em; /* 224px */
  background: rgba(237, 182, 44);
  padding: 0.625em; /* 10px */
  margin: 0 1.25em 1.25em 0;
  border-radius: 1em; /* 16px */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  font-size: 0.875rem;
}

.date {
  font-size: 0.5rem;
  font-weight: bold;
  letter-spacing: 1px;
}
</style>
