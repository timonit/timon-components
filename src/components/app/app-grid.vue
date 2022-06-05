<template>
  <div class="grid">
    <slot></slot>
  </div>
</template>

<style scope lang="scss">
.grid {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-auto-rows: minmax(50px, auto);
}
</style>
