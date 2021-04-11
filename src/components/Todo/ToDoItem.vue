<template>
  <div class="app__item">
      {{ item }}
    <FontAwesomeIcon
      class="app__icon"
      :icon="myIcon"
      @click="deleteTask(item)"
    />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';
import { Prop } from 'vue-property-decorator';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import {
  faTrash,
} from '@fortawesome/free-solid-svg-icons';

@Component({
  components: {
    FontAwesomeIcon,
    faTrash,
  },
})
export default class ToDoItem extends Vue {
  @Prop()
  private item?: null;

  private myIcon = faTrash;

  deleteTask(id: string) {
    this.$emit('deleteTask', id);
  }
}
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";

  .app__item {
    padding: 20px;
    display: flex;
    justify-content: space-between;
    background: $color-white;
    border-radius: $borderRadius;
    align-items: center;

    & + .app__item {
      margin-top: 15px;
    }
  }
</style>
