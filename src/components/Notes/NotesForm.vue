<template>
  <div class="note-form__wrapper">
    <form class="note-form" @submit.prevent="onSubmit">
      <textarea v-model="value" placeholder="Сделайте запись" />
      <TagsList :items="tags" @onItemClick="handlerTags" isActiveItem />
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
      const title = this.value;
      const tag = this.tag;
      this.$emit('onSubmit', { title, tag });
      // console.log(this.value);
      //переведи this.value в title, согласно переменным выше
      this.value = '';
      this.tag = '';
    },
    handlerTags(tag) {
      console.log(tag);
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
