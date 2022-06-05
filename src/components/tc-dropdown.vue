<template>
  <div class="dropdown">
    <label for="dropdown-input">
      <input
        disabled
        type="text"
        :value="modelValue"
        @input="$emit(
          'update:modelValue',
          ($event.target as HTMLInputElement)?.value
        )"
        id="dropdown-input"
        :placeholder="placeholder"
      />
    </label>
    <button @click="toggle">
      <i v-show="isShow" class="fa-solid fa-minus"></i>
      <i v-show="!isShow" class="fa-solid fa-angle-down"></i>
    </button>
    <div class="list" v-show="isShow">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    placeholder: String,
    modelValue: String,
  },
  emits: ['update:modelValue'],
  data() {
    return {
      isShow: false,
    };
  },
  methods: {
    toggle() {
      if (this.isShow) this.hideList();
      else this.showList();
    },
    showList() {
      this.isShow = true;
    },
    hideList() {
      this.isShow = false;
    },
  },
});
</script>

<style lang="scss" scope>
.dropdown {
  position: relative;
  background-color: rgb(245, 245, 245);
  display: flex;
  height: 1.5em;
  align-items: center;

  input {
    padding: 0 5px;
    border: none;
    min-width: 100px;
    background-color: none;
  }

  button {
    background-image: url("https://www.flaticon.com/ru/free-icon/drop-down-arrow_60995?term=%D0%B2%D0%BD%D0%B8%D0%B7&page=1&position=8&page=1&position=8&related_id=60995&origin=search#");
    border: none;
    cursor: pointer;
    width: 1.5em;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

    &:hover {
      background-color: gray;
    }
  }

  .list {
    position: absolute;
    background-color: red;
    top: 100%;
    left: 0;
    display: flex;
    flex-direction: column;
  }
}
</style>
