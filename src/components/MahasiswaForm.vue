<template>
  <form v-on:submit.prevent="submitMahasiswa">
    <div class="six columns">
      <p v-if="error && submitting" class="error-message">
        Oops, ada yang kosong!!
      </p>
      <p v-if="success" class="success-message">Berhasil Ditambah</p>
      <label for="inputNama">Nama Mahasiswa</label>
      <input
        v-model="mahasiswa.nama"
        class="u-full-width"
        :class="{ 'has-error': submitting && invalidNama }"
        type="text"
        placeholder="Masukan Nama...."
        id="inputNama"
      />

      <label for="inputNim">NIM</label>
      <input
        v-model="mahasiswa.nim"
        class="u-full-width"
        :class="{ 'has-error': submitting && invalidNim }"
        type="text"
        placeholder="Masukan NIM...."
        id="inputNim"
      />

      <label for="inputEmail">Email Mahasiswa</label>
      <input
        v-model="mahasiswa.email"
        class="u-full-width"
        :class="{ 'has-error': submitting && invalidEmail }"
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
      submitting: false,
      error: false,
      success: false,
      mahasiswa: {
        nama: "",
        nim: "",
        email: "",
      },
    };
  },

  methods: {
    submitMahasiswa() {
      this.submitting = true;
      this.clearStatus();

      // validasi
      if (this.invalidNama || this.invalidNim || this.invalidEmail) {
        this.error = true;
        return;
      }
      this.$emit("add:mahasiswa", this.mahasiswa);
      this.clearMahasiswa();

      //set sukses
      this.success = true;
      this.error = false;
      this.submitting = false;
    },
    clearStatus() {
      this.error = false;
      this.success = false;
    },

    clearMahasiswa() {
      this.mahasiswa = {
        nama: "",
        nim: "",
        email: "",
      };
    },
  },

  computed: {
    invalidNama() {
      return this.mahasiswa.nama == "";
    },
    invalidNim() {
      return this.mahasiswa.nim == "";
    },
    invalidEmail() {
      return this.mahasiswa.email == "";
    },
  },
};
</script>

<style scoped>
[class*="-message"] {
  font-weight: 500;
}

.error-message {
  color: red;
}

.success-message {
  color: green;
}

input.has-error {
  border: 1.5px solid red;
}
</style>