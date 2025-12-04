<template>
  <footer class="footer">
    <div class="container footer-content">
      <div class="footer-grid">
        <div class="footer-section">
          <h3 class="footer-title">Poetnam Shop</h3>
          <p class="footer-text">
            Toko online terpercaya untuk gamis dan kerudung berkualitas
          </p>
        </div>

        <div class="footer-section">
          <h4 class="footer-heading">Kontak</h4>
          <p class="footer-text">Blok V 00 Citra Indah 16830</p>
          <p class="footer-text">Kota Bogor, Jawa Barat</p>
          <p class="footer-text">+62 813-1694-326</p>
        </div>

        <div class="footer-section">
          <h4 class="footer-heading">Link Cepat</h4>
          <router-link to="/" class="footer-link">Home</router-link>
          <router-link to="/products" class="footer-link">Produk</router-link>
          <router-link to="/about" class="footer-link">Tentang</router-link>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; 2024 Poetnam Shop. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: linear-gradient(to right, #1f2937, #111827);
  color: white;
  padding: 3rem 0 2rem;
  margin-top: auto;
}

.footer-content {
  padding: 0 1rem;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-bottom: 2rem;
}

.footer-section {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.footer-title {
  font-size: 1.5rem;
  font-weight: 700;
  background: linear-gradient(to right, #fda4af, #c084fc);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
}

.footer-heading {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.footer-text {
  color: #d1d5db;
  line-height: 1.75;
}

.footer-link {
  color: #d1d5db;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-link:hover {
  color: #fda4af;
}

.footer-bottom {
  border-top: 1px solid #374151;
  padding-top: 2rem;
  text-align: center;
  color: #9ca3af;
}
</style>