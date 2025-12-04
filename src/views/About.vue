<template>
  <div class="about-page">
    <div class="container">
      <h1 class="page-title animate-slideInDown">Tentang Poetnam Shop</h1>

      <div class="about-content animate-fadeInUp">
        <p class="about-text">
          Poetnam Shop adalah toko online terpercaya yang menyediakan koleksi gamis dan kerudung 
          berkualitas tinggi dengan harga terjangkau. Kami berkomitmen untuk memberikan pelayanan 
          terbaik kepada pelanggan dengan produk-produk pilihan yang mengutamakan kenyamanan dan 
          keindahan dalam berbusana muslim.
        </p>
        <p class="about-text">
          Setiap produk yang kami tawarkan telah melalui proses seleksi ketat untuk memastikan 
          kualitas bahan, jahitan, dan desain yang sesuai dengan standar fashion muslim modern. 
          Kepuasan pelanggan adalah prioritas utama kami.
        </p>
      </div>

      <div class="contact-section animate-fadeInUp animation-delay-200">
        <h2 class="contact-title">Hubungi Kami</h2>
        
        <div class="contact-items">
          <div class="contact-item">
            <MapPin :size="28" class="contact-icon" />
            <div>
              <h3 class="contact-label">Alamat</h3>
              <p class="contact-value">
                Blok V 00 Citra Indah 16830<br />
                Kota Bogor, Jawa Barat
              </p>
            </div>
          </div>

          <div class="contact-item">
            <Phone :size="28" class="contact-icon" />
            <div>
              <h3 class="contact-label">Telepon</h3>
              <p class="contact-value">+62 813-1694-326</p>
            </div>
          </div>

          <div class="contact-item">
            <Mail :size="28" class="contact-icon" />
            <div>
              <h3 class="contact-label">Email</h3>
              <p class="contact-value">info@poetnamshop.com</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { MapPin, Phone, Mail } from 'lucide-vue-next'
</script>

<style scoped>
.about-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 100%);
  padding: 5rem 0;
  animation: fadeIn 0.6s ease-out;
}

.page-title {
  font-size: 3rem;
  font-weight: 700;
  text-align: center;
  color: #1f2937;
  margin-bottom: 4rem;
}

.about-content {
  background: white;
  border-radius: 1rem;
  padding: 2rem;
  margin-bottom: 2rem;
}

.about-text {
  font-size: 1.125rem;
  color: #374151;
  line-height: 1.75;
  margin-bottom: 1rem;
}

.about-text:last-child {
  margin-bottom: 0;
}

.contact-section {
  background: white;
  border-radius: 1rem;
  padding: 2rem;
}

.contact-title {
  font-size: 1.875rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 1.5rem;
}

.contact-items {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}

.contact-icon {
  color: #ec4899;
  flex-shrink: 0;
  margin-top: 0.25rem;
}

.contact-label {
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 0.25rem;
  font-size: 1.125rem;
}

.contact-value {
  color: #4b5563;
  line-height: 1.75;
}

@media (max-width: 768px) {
  .about-page {
    padding: 3rem 0;
  }

  .page-title {
    font-size: 2rem;
  }

  .about-content,
  .contact-section {
    padding: 1.5rem;
  }
}
</style>