<template>
  <button
    class="btn btn-primary"
    @click="addNewTask"
    :disabled="disabled"
  >
    {{ text }}
  </button>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';
import { Prop } from 'vue-property-decorator';

@Component()
export default class ButtonTemplate extends Vue {
  @Prop()
  private text: string;

  @Prop({ required: true }) readonly disabled: boolean

  addNewTask() {
    this.$emit('addNewTask');
  }
}
</script>
