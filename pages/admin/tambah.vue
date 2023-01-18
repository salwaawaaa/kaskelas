<template>
  <navbar />
  <div>
    <h1>Bayar Kas</h1>
    <form @submit.prevent="tambah()">
      <input v-model="nama" placeholder="nama" /> <br />
      <input v-model="tanggal" placeholder="tanggal" /> <br />
      <input v-model="nominal" placeholder="nominal" /> <br />
      <button type="submit">Tambah</button>
      <NuxtLink to="/">Kembali</NuxtLink>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama = ref();
const tanggal = ref();
const nominal = ref();

async function tambah() {
  await supabase.from("kas").insert({
    nama: nama.value,
    tanggal: tanggal.value,
    nominal: nominal.value,
  });
  navigateTo("/");
}
</script>
