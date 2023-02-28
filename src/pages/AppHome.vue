<template lang="pug">
Form(@onSubmit="handleSubmit")
List(@onRemove="handleRemove" :items="notes")
</template>

<script lang="ts">
import Form from "@/components/Notes/NotesForm.vue";
import List from "@/components/Notes/NotesList.vue";

export default {
  components: { Form, List },
  data() {
    return {
      notes: [
        {
          title: "Learn vue 3",
          tags: ["work", "study"],
        },
        {
          title: "Drink coffee",
          tags: ["home"],
        },
      ],
    };
  },
  mounted() {
    this.getNotes();
  },
  watch: {
    notes: {
      handler(updatedList) {
        localStorage.setItem("notes", JSON.stringify(updatedList));
      },
      deep: true,
    },
  },
  methods: {
    getNotes() {
      const localNotes = localStorage.getItem("notes");
      if (localNotes) {
        this.notes = JSON.parse(localNotes);
      }
    },
    handleSubmit({ title, tags }) {
      const note = {
        title,
        tags,
      };
      console.log(note);
      this.notes.push(note);
    },
    handleRemove(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>
