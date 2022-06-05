<template>
  <div class="card">
    <span v-if="label">{{ label }}</span>
    <div class="body">
      <slot></slot>
    </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    label: String,
  },
});
</script>

<style scope lang='scss'>
$border: rgb(200,200,200);

.card {
  display: flex;
  flex-direction: column;
  border: solid 1px $border;
  padding: 10px;
  justify-content: center;

  span {
    width: 100%;
  }

  .body {
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>
