<template>
  <div class="container">
    <app-header />
    <add-new-note @addNote="addNewNote" />
    <app-note :notes="notes" @deleteNote="deleteNote" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import NoteGrid from "./components/NoteGrid.vue";
import AddNote from "./components/AddNote.vue";

export default {
  components: {
    appHeader: Header,
    appFooter: Footer,
    appNote: NoteGrid,
    addNewNote: AddNote,
  },
  data() {
    return {
      notes: [],
    };
  },
  mounted() {
    if (localStorage.getItem("notes")) {
      try {
        this.cats = JSON.parse(localStorage.getItem("notes"));
      } catch (e) {
        localStorage.removeItem("notes");
      }
    }
  },
  methods: {
    addNewNote(note) {
      this.notes.push(note);
      this.saveNote();
    },
    deleteNote(index) {
      if (confirm("Are you sure you want to delete this note?")) {
        this.notes.splice(index, 1);
      }
    },
    saveNote() {
      const parsed = JSON.stringify(this.notes);
      localStorage.setItem("notes", parsed);
    },
  },
};
</script>

<style>
bpdy {
  margin: 0;
}
</style>
