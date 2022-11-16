<template>
  <div id="app">
    <div class="container">
      <h1>Mahasiswa</h1>
      <mahasiswa-table v-bind:data="datamahasiswa" />
    </div>
  </div>
</template>

<script>
import MahasiswaTable from "@/components/MahasiswaTable.vue";

export default {
  name: "App",
  components: {
    MahasiswaTable,
  },
  data() {
    return {
      datamahasiswa: [
        {
          id: 1,
          nama: "Eka Wardana",
          nim: "11183102",
          email: "eka@gmail.com",
        },
        {
          id: 2,
          nama: "Shenny Risky",
          nim: "11192810",
          email: "shenny@gmail.com",
        },
      ],
    };
  },
};
</script>

<style scoped>
</style>
