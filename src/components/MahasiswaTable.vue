<template>
  <div id="mhs-table">
    <table class="u-full-width">
      <thead>
        <tr>
          <th>Nama</th>
          <th>Nim</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="mahasiswa in data" :key="mahasiswa.id">
          <td>{{ mahasiswa.nama }}</td>
          <td>{{ mahasiswa.nim }}</td>
          <td>{{ mahasiswa.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "mahasiswa-table",
  props: ["data"],
};
</script>

<style>
</style>