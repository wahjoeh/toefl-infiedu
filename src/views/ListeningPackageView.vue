<script setup>
import logo from '../assets/logo.png'
import { useRouter } from 'vue-router'

const router = useRouter()

const packages = [
  {
    id: 'paket-soal-1',
    title: 'Paket Soal 1',
    description: '40 Questions',
    locked: false
  },
  {
    id: 'paket-soal-2',
    title: 'Paket Soal 2',
    description: '40 Questions',
    locked: true
  }
]

const openPackage = (pkg) => {
  if (pkg.locked) return

  router.push(`/listening/${pkg.id}`)
}
</script>

<template>

  <header class="cbt-header">

    <div class="header-left">

      <div class="logo-box">
        <img
          :src="logo"
          class="logo-image"
        />
      </div>

      <div>

        <h1 class="header-title">
          Listening Section
        </h1>

        <p class="header-subtitle">
          TEP Exercise Online
        </p>

      </div>

    </div>

  </header>

  <div class="package-page">

    <div class="package-wrapper">

      <h2 class="page-title">
        Pilih Paket Soal Listening
      </h2>

      <div class="package-grid">

        <div
          v-for="pkg in packages"
          :key="pkg.id"
          class="package-card"
          :class="{ locked: pkg.locked }"
          @click="openPackage(pkg)"
        >

          <div class="package-icon">
            🎧
          </div>

          <h3>
            {{ pkg.title }}
          </h3>

          <p>
            {{ pkg.description }}
          </p>

          <button
            class="start-btn"
            :disabled="pkg.locked"
          >
            {{ pkg.locked ? 'Locked' : 'Mulai Listening Test' }}
          </button>

        </div>

      </div>

    </div>

  </div>

</template>

<style src="../assets/reading-package.css"></style>