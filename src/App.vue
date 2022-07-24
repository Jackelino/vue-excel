<script>
import HelloWorld from './components/HelloWorld.vue';
import xlsx from 'xlsx/dist/xlsx.full.min';

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      framework: [
        {name: "George Washington", birthday: "1732-02-22"},
        {name: "John Adams", birthday: "1735-10-19"},
      ]
    }
  },
  methods: {
    exportExcel() {
      const XLSX = xlsx;
      const workbook = XLSX.utils.book_new();
      const worksheet = XLSX.utils.json_to_sheet(this.framework);
      XLSX.utils.book_append_sheet(workbook, worksheet, "framework");
      XLSX.writeFile(workbook, "framework.xlsx");
    }
  }
}
</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo"/>
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo"/>
    </a>
  </div>
  <HelloWorld msg="Vite + Vue"/>
  <button @click.prevent="exportExcel">excel</button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
