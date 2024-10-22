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
      notes: [
        {
          title: 'Выучить Vue 3',
          tags: ['work'],
        },
        {
          title: 'Закончить курс',
          tags: ['work', 'home'],
        },
        {
          title: 'Домашняя уборка',
          tags: [],
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
        localStorage.setItem('notes', JSON.stringify(updatedList));
      },
      deep: true,
    },
  },
  components: {
    Form,
    List,
  },
  methods: {
    // submit note
    handleSubmit({ title, tag }) {
      const tagsArray = [];
      tagsArray.push(tag);
      const note = {
        title: title,
        tags: [tag],
      };
      console.log(title);
      console.log(tag);
      this.notes.push(note);
    },
    // remove note
    handleRemove(index) {
      this.notes.splice(index, 1);
    },
    // get/set notes
    getNotes() {
      const localNotes = localStorage.getItem('notes');
      if (localNotes) {
        this.notes = JSON.parse(localNotes);
      }
    },
  },
};
</script>
