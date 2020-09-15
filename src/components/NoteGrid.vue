<template>
  <div>
    <app-note v-for="(note, index) in notes" :key="note.index">
      <h1>{{note.title | capitalize}}</h1>
      <hr />
      <p>{{note.content | capitalize}}</p>
      <button @click="deleteNote(index)">x</button>
    </app-note>
  </div>
</template>

<script>
import Note from "./Note.vue";

export default {
  components: {
    appNote: Note,
  },
  props: ["notes"],
  methods: {
    deleteNote(index) {
      this.$emit("deleteNote", index);
    },
  },
  filters: {
    capitalize: function (value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
};
</script>

<style scoped>
slot h1 {
  font-size: 1.1em;
  margin: 0;
}
slot p {
  font-size: 1.1em;
  margin-bottom: 10px;
  white-space: pre-wrap;
  word-wrap: break-word;
}
button {
  position: relative;
  float: right;
  margin-right: 10px;
  background-color: #f5ba13;
  color: white;
  border: none;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  cursor: pointer;
  outline: none;
}
</style>