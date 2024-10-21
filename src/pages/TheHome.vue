<template>
  <Form @onSubmit="handleSubmit" />
  <List @onRemove="handleRemove" :items="notes" />
</template>

<script>
import Form from '@/components/Notes/NotesForm';
import List from '@/components/Notes/NotesList';

export default {
  data() {
    return {
      notes: ['task 1', 'task 2', 'task 3'],
    };
  },
  components: {
    Form,
    List,
  },
  methods: {
    handleSubmit(note) {
      this.notes.push(note);
    },
    handleRemove(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>
