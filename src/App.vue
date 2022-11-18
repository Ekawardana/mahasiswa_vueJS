<template>
  <div id="app">
    <div class="container">
      <h1>Data Mahasiswa</h1>
      <mahasiswa-form @add:mahasiswa="addMahasiswa" />
      <mahasiswa-table
        v-bind:data="datamahasiswa"
        @delete:mahasiswa="deleteMahasiswa"
      />
    </div>
  </div>
</template>

<script>
import MahasiswaTable from "@/components/MahasiswaTable.vue";
import MahasiswaForm from "@/components/MahasiswaForm.vue";

export default {
  name: "App",
  components: {
    MahasiswaTable,
    MahasiswaForm,
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

  methods: {
    addMahasiswa(mahasiswa) {
      /** Kondisi, jika data yang diterima > 0(True)
       * maka tampil [this.datamahasiswa.length - 1]
       * jika tidak maka data 0(Kosongin aja).
       * **/
      const lastId =
        this.datamahasiswa.length > 0
          ? this.datamahasiswa[this.datamahasiswa.length - 1].id
          : 0;
      // id terakhir yang ada di array tambah 1 buat dapetin id baru
      const id = lastId + 1;

      const newMahasiswa = { ...mahasiswa, id };

      // Panggil data yg ditampung divariable newMahasiswa
      this.datamahasiswa = [...this.datamahasiswa, newMahasiswa];
    },

    deleteMahasiswa(id) {
      // Modal
      var resconfirm = confirm("Apakah Anda Yakin?");
      if (resconfirm) {
        // Aksi Delete Mahasiswa
        this.datamahasiswa = this.datamahasiswa.filter(
          (mahasiswa) => mahasiswa.id !== id
        );
      }
    },
  },
};
</script>

<style scoped>
</style>
