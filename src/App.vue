<template>
  <div id="app">
    <div class="app__container">
      <div class="app__modal">
        <h1 class="app__title">
          TO-DO LIST
        </h1>
        <div class="app__task">
          <InputTemplate
            :type="'text'"
            :focus="true"
            :placeholder="'Enter your task'"
            :value.sync="model"
          />
          <ButtonTemplate
            :text="'Add'"
            @addNewTask="addNewTask"
            :disabled="model === ''"
          />
        </div>
        <div class="app__content"
             v-if="tasksList.length"
        >
          <ToDoList
            :tasksList="listTasks"
            @deleteTask="deleteTask"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import ButtonTemplate from '@/components/Button/ButtonTemplate.vue';
import InputTemplate from '@/components/Input/InputTemplate.vue';
import ToDoList from '@/components/Todo/TodoList.vue';

@Component({
  components: {
    ButtonTemplate,
    InputTemplate,
    ToDoList,
  },
})
export default class App extends Vue {
  public tasksList: [] = [];

  public model = '';

  get listTasks(): [] {
    return this.tasksList;
  }

  addNewTask(): [] {
    this.tasksList.push(this.model);
    this.model = '';
  }

  deleteTask(id: string): [] {
    this.tasksList = this.tasksList.filter((item) => item !== id);
  }
}

</script>

<style lang="scss">
@import '@/assets/scss/style.scss';

</style>
