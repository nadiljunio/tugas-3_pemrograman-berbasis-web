<script setup>
import MyFooter from '@/components/MyFooter.vue';
import { ref, onMounted } from 'vue';


const greeting = ref("");

onMounted(() => {
  const namaUser = localStorage.getItem("namaUser");
  const hours = new Date().getHours();

  let message =
    hours < 11
      ? "Selamat Pagi"
      : hours < 15
        ? "Selamat Siang"
        : hours < 19
          ? "Selamat Sore"
          : "Selamat Malam";
  greeting.value = `${message}, ${namaUser || "Tamu"}!`;
});
</script>

<template>
  <main>
        <div class="hero container">
            <h1>Selamat Datang</h1>
            <p>Sistem Manajemen Stok dan Tracking Terintegrasi</p>

            <div class="card-container">
                <div class="card">
                    <h2>📦 Stok Barang</h2>
                    <p>Kelola dan pantau stok barang Anda dengan mudah. Tambah, edit, dan hapus data stok secara real-time.</p>
                    <router-link class="card-link" to="/stock">Informasi Bahan Ajar</router-link>

                </div>

                <div class="card">
                    <h2>🚚 Tracking</h2>
                    <p>Lacak pengiriman dan status barang Anda. Pantau perjalanan barang dari gudang hingga tujuan.</p>
                     <router-link class="card-link" to="/tracking">Tracking Pengiriman</router-link>
                </div>
            </div>
        </div>
    </main>

<MyFooter />
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 92vh;
  height: 100%;
  flex-grow: 1;
}
.hero {
    text-align: center;
    color: rgb(0, 0, 0);
    max-width: 800px;
}

.hero h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    margin-top: 3rem;
}

.hero p {
    font-size: 1.2rem;
    margin-bottom: 2rem;
    opacity: 0.9;
        }

.card-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    margin-top: 3rem;
}

.card {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    cursor: pointer;
}

.card:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
}

.card h2 {
    color: #667eea;
    margin-bottom: 1rem;
    font-size: 1.5rem;
}

.card p {
    color: #666;
    line-height: 1.6;
    margin-bottom: 1rem;
}

.card-link {
    display: inline-block;
    background: #667eea;
    color: white;
    padding: 0.7rem 1.5rem;
    border-radius: 5px;
    text-decoration: none;
    font-weight: 500;
    transition: background 0.3s ease;
}

.card-link:hover {
    background: #764ba2;
}



@media (max-width: 768px) {
    .hero h1 {
        font-size: 2rem;
    }

    .hero p {
        font-size: 1rem;
    }

    .nav-menu {
        gap: 1rem;
    }
}
</style>
