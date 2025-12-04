<template>
  <div class="hero">
    <div class="blob blob-1"></div>
    <div class="blob blob-2"></div>
    <div class="blob blob-3"></div>

    <div class="container hero-content">
      <div class="hero-text animate-slideInLeft">
        <h1 class="hero-title">
          Koleksi <span class="text-pink">Gamis</span> & 
          <span class="text-purple">Kerudung</span> Terbaik
        </h1>
        <p class="hero-description">
          Tampil anggun dan syar'i dengan koleksi fashion muslim terkini dari Poetnam Shop
        </p>
        <router-link to="/products" class="btn-primary">
          Lihat Koleksi
        </router-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
.hero {
  position: relative;
  height: 600px;
  background: linear-gradient(135deg, #fce7f3 0%, #f3e8ff 50%, #fce7f3 100%);
  overflow: hidden;
}

.blob {
  position: absolute;
  width: 24rem;
  height: 24rem;
  border-radius: 9999px;
  mix-blend-mode: multiply;
  filter: blur(80px);
  opacity: 0.1;
}

.blob-1 {
  top: 0;
  left: 0;
  background: #ec4899;
  animation: blob 7s infinite;
}

.blob-2 {
  top: 0;
  right: 0;
  background: #9333ea;
  animation: blob 7s infinite;
  animation-delay: 2s;
}

.blob-3 {
  bottom: 0;
  left: 50%;
  background: #fda4af;
  animation: blob 7s infinite;
  animation-delay: 4s;
}

.hero-content {
  position: relative;
  height: 100%;
  display: flex;
  align-items: center;
}

.hero-text {
  max-width: 42rem;
}

.hero-title {
  font-size: 3.75rem;
  font-weight: 700;
  color: #1f2937;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.text-pink {
  color: #ec4899;
}

.text-purple {
  color: #9333ea;
}

.hero-description {
  font-size: 1.25rem;
  color: #4b5563;
  margin-bottom: 2rem;
  line-height: 1.75;
}

@media (max-width: 768px) {
  .hero {
    height: 500px;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-description {
    font-size: 1.125rem;
  }
}
</style>