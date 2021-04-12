<template>
    <input :type="type"
           class="form-control"
           :autofocus="focus"
           v-model="model"
           :placeholder="placeholder">
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';
import { Prop, PropSync } from 'vue-property-decorator';

@Component()
export default class InputTemplate extends Vue {
  @Prop({ required: true }) readonly type: string

  @Prop({ required: true, default: false }) readonly focus: boolean

  @Prop({ required: true, default: true }) readonly placeholder: boolean

  @PropSync('value', { type: String }) model!: string
}
</script>
