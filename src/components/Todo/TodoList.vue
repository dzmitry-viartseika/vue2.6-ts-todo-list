<template>
  <div class="app__list">
    <ToDoItem
      :key="item"
      :item="item"
      v-for="item in tasksList"
      @deleteTask="deleteTask"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';
import ToDoItem from '@/components/Todo/ToDoItem.vue';
import { Prop } from 'vue-property-decorator';

@Component({
  components: {
    ToDoItem,
  },
})
export default class TodoList extends Vue {
  @Prop()
  private tasksList: [];

  deleteTask(id: string) {
    this.$emit('deleteTask', id);
  }
}
</script>
