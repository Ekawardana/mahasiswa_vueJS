<template>
  <form v-on:submit.prevent="submitMahasiswa">
    <div class="six columns">
      <label for="inputNama">Nama Mahasiswa</label>
      <input
        v-model="mahasiswa.nama"
        class="u-full-width"
        type="text"
        placeholder="Masukan Nama...."
        id="inputNama"
      />

      <label for="inputNim">NIM</label>
      <input
        v-model="mahasiswa.nim"
        class="u-full-width"
        type="text"
        placeholder="Masukan NIM...."
        id="inputNim"
      />

      <label for="inputEmail">Email Mahasiswa</label>
      <input
        v-model="mahasiswa.email"
        class="u-full-width"
        type="text"
        placeholder="Masukan Email...."
        id="inputEmail"
      />

      <button class="button-primary">Add Mahasiswa</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "mahasiswa-form",
  data() {
    return {
      mahasiswa: {
        nama: "",
        nim: "",
        email: "",
      },
    };
  },
  methods: {
    submitMahasiswa() {
      this.$emit("add:mahasiswa", this.mahasiswa);
    },
  },
};
</script>

<style>
</style>