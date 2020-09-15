<template>
  <div>
    <form class="add-note">
      <input type="text" name="title" placeholder="Title" v-model="note.title" />
      <hr />
      <textarea
        name="content"
        cols="30"
        rows="3"
        v-model="note.content"
        placeholder="Take a note ..."
      ></textarea>
      <button @click.prevent="createNew">+</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      note: {
        title: "",
        content: "",
      },
    };
  },
  methods: {
    createNew() {
      if (this.note.title !=="") {
        this.$emit("addNote", this.note);
        this.note = {};
      } else {
        alert("Please input something.");
      }
    },
  },
};
</script>
<style scoped>
hr {
  margin: 0;
}
.add-note {
  position: relative;
  width: 480px;
  margin: 30px auto 20px auto;
  background: #fff;
  padding: 10px;
  border-radius: 7px;
  box-shadow: 0 1px 5px rgb(138, 137, 137);
}

.add-note input,
.add-note textarea {
  width: 100%;
  border: none;
  padding: 4px;
  outline: none;
  font-size: 1.2em;
  font-family: inherit;
  resize: none;
}

.add-note button {
  position: absolute;
  right: 18px;
  bottom: 18px;
  background: #f5ba13;
  color: #fff;
  border: none;
  border-radius: 50%;
  width: 36px;
  height: 36px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
  cursor: pointer;
  outline: none;
}
</style>