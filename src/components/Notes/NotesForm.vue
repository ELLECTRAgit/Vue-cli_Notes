<template>
  <div class="note-form__wrapper">
    <form class="note-form" @submit.prevent="onSubmit">
      <textarea v-model="value" placeholder="Сделайте запись" />
      <TagsList :items="tags" @onItemClick="handlerTags" />
      <button class="btn btnPimary" type="submit">Добавьте запись</button>
    </form>
  </div>
</template>
<script>
import TagsList from '@/components/UI/TagsList.vue';
export default {
  components: {
    TagsList,
  },
  data() {
    return {
      value: '',
      tags: ['home', 'work', 'travel'],
    };
  },
  methods: {
    onSubmit() {
      this.$emit('onSubmit', this.value);
      console.log(this.value);
      this.value = '';
    },
    handlerTags(tag) {
      console.log(tag);
      const itemsTags = document.querySelectorAll('.tag-item');
      console.log(itemsTags);
      itemsTags.forEach((item) => {
        item.addEventListener('click', () => {
          item.classList.toggle('isActiveItem');
        });
      });
    },
  },
};
</script>
<style>
.note-form {
  max-width: 600px;
  width: 100%;
  display: flex;
  flex-direction: column;
}
.note-form__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
