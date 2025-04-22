<script setup>
import { ref, onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const videoPlayer = ref(1)

onMounted(() => {
   
})

watch(() => route.path, (newPath) => {
  
}, { immediate: true })


 


 
videoPlayer.value = Math.floor(Math.random() * 4) + 1
 
const wpGonder = () => {

  function openWhatsApp() {
  const phoneNumber = '+905300652957'; // Telefon numaranızı buraya yazın
  const message = 'Merhaba, bilgi almak istiyor dum?'; // Mesajınızı burada özelleştirebilirsiniz
  const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
  
  window.open(url, '_blank');
}
openWhatsApp(); 

}


</script>

<template>
  <div >
    <div class="h-[90vh]" >
    <div :class="['video-wrapper', route.path != '/' ? 'lightBar' : '']">
      <header class="p-4 text-black">
        <video autoplay muted loop playsinline>
          <source :src="`/_nuxt/assets/img/video${videoPlayer}.mp4`" type="video/mp4" />
          Tarayıcınız video etiketini desteklemiyor.
        </video>

        <nav class="relative z-50 flex items-center justify-center gap-4">
          <NuxtLink class="nuxtlink" to="/">Anasayfa</NuxtLink>
          <NuxtLink to="/hakkimizda" class="nuxtlink">Hakkımızda</NuxtLink>
          <NuxtLink to="/iletisim" class="nuxtlink">İletişim</NuxtLink>
        </nav>
      </header>

      <section class="h-full">
        <div class="h-[calc(100%-30%)] flex items-center justify-center">
          <div class="banner">
            <h1 class="title">ÇINAR ELEKTRİK</h1>
            <p class="subtitle">Güvenilir ve kaliteli elektrik çözümleri</p>
            <p class="description">
              Bireysel ve kurumsal müşterilerimize, ihtiyaçlarına özel çözümler sunarak; projelendirme, montaj, bakım ve arıza hizmetlerinde
              yüksek kalite standartlarını benimsiyoruz. Elektrikte güvenin ve profesyonelliğin adresi Çınar Elektrik, her zaman yanınızda.
            </p>
            <button class="mt-3 bg-blue-200 p-3 hover:opacity-50 hover:cursor-pointer rounded-2xl transition-all 1s ease-in" v-on:click="wpGonder">İletişime Geç</button>
          </div>
        </div>
      </section>
    </div>

    <main class="">
      <NuxtPage />
    </main>
  </div>

  <div class="h-[10vh]">
    <footer class="p-4 h-full flex items-center justify-center bg-gray-100 text-center text-sm">
      © 2025 - Tüm Hakları Saklıdır 
    </footer>
  </div>
  </div>
</template>

<style scoped>
.video-wrapper {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background-color: rgba(0, 0, 0, 0.164);
}


.video-wrapper.lightBar{
height: 60px;
background-color: rgba(0, 0, 0, 0.644);
}

.video-wrapper.lightBar .banner{
display: none;
}

.video-wrapper.lightBar .nuxtlink{
color:white !important;
font-weight: 700 ;
}



.video-wrapper video {
  position: absolute;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  transform: translate(-50%, -50%);
  object-fit: cover;
  z-index: -1;
}

.nuxtlink {
  color: rgba(255, 255, 255, 0.6);
  font-size: .9em;
}
.nuxtlink:hover {
  color: white;
  cursor: pointer;
  transition: all 1s ease;
}

.banner {
  position: relative;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  text-align: center;
}

.title {
  font-size: 4rem;
  font-weight: bold;
  color: white;
  animation: slideFromLeft 1.5s ease-out forwards;
  opacity: 0;
}

.subtitle {
  font-size: 1.8rem;
  color: white;
  margin-top: 1rem;
  animation: slideFromRight 1.5s ease-out forwards;
  opacity: 0;
}

@keyframes slideFromLeft {
  0% { transform: translateX(-100%); opacity: 0; }
  100% { transform: translateX(0); opacity: 1; }
}

@keyframes slideFromRight {
  0% { transform: translateX(100%); opacity: 0; }
  100% { transform: translateX(0); opacity: 1; }
}

.description {
  font-size: 1.2rem;
  color: white;
  max-width: 700px;
  margin-top: 1rem;
  padding: 0 1rem;
  animation: fadeIn 2s ease-out forwards;
  opacity: 0;
}

@keyframes fadeIn {
  0% { opacity: 0; transform: translateY(20px); }
  100% { opacity: 1; transform: translateY(0); }
}
</style>
