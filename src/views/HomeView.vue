<template>
  <app-grid>
    <app-card label="dropdown">
      <tc-dropdown class="dr" v-model="name" placeholder="timon">
        <span
          v-for="name of names"
          :key="name"
          @click="pick(name)"
          @keydown="undefined"
        >{{ name }}</span>
      </tc-dropdown>
    </app-card>
  </app-grid>
</template>

<script lang='ts'>
import AppCard from '@/components/app/app-card.vue'; // @ is an alias to /src
import AppGrid from '@/components/app/app-grid.vue';
import tcDropdown from '@/components/tc-dropdown.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  components: {
    AppCard,
    AppGrid,
    tcDropdown,
  },
  data() {
    return {
      names: ['asd', 'dsa', 'ddd', 'aaa'],
      name: 'asd',
    };
  },
  methods: {
    pick(name: string) {
      this.name = name;
    },
  },
});
</script>

<style lang="scss" scope>
span {
  padding: 0 5px;
  cursor: pointer;
}
</style>
