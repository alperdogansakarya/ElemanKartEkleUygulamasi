<template >
    <div>
        <!-- Kullanıcıdan eleman bilgilerini girebileceği inputlar -->
        <div>
            <input v-model="ad" placeholder="Adınız">
            <input v-model="soyad" placeholder="Soyadınız">
            <input v-model="yazilimDilleri" placeholder="Bildiğiniz Yazılım Dilleri">
            <input v-model="deneyim" placeholder="Deneyim Süreniz(Yıl)">
            <button @click="elemanEkle">Eleman Ekle</button>
        </div>

        <div>
            <div v-for="(eleman, index) in elemanlar" :key="index" class="eleman-karti"> <!-- Elemanlar diye bir dizimiz var burada eleman ve index dönülüyor.-->
                <h3>{{ eleman.ad }} {{ eleman.soyad }}</h3>
                <p>Bildiği Diller: {{ eleman.yazilimDilleri }}</p>
                <p>Deneyim Süresi: {{ eleman.deneyim }}</p>
            </div>
        </div>
    </div>
</template>
<script>
import { ref } from 'vue';

export default {
    setup() {
        //Kullanıcı girişlerini tutacak değişkenlerimiz burada yer alıyor.

        const ad = ref('');
        const soyad = ref('');
        const yazilimDilleri = ref('');
        const deneyim = ref(0);
        const elemanlar = ref([]);  // eleman bilgilerini tutacak dizimiz şuan için içi boş.

        // Eleman ekle butonuna tıklandığında çalışacak fonksiyon
        const elemanEkle = () => {
            // Girilen bilgileri elemanlar dizisine ekleyeceğiz.
            elemanlar.value.push({
                ad: ad.value,
                soyad: soyad.value,
                yazilimDilleri: yazilimDilleri.value,
                deneyim: deneyim.value
            });

            //Veri girişi sonrası input alanlarını temizle 
            ad.value = '';
            soyad.value = '';
            yazilimDilleri.value = '';
            deneyim.value = 0;
        };

        return {
            ad,
            soyad,
            deneyim,
            yazilimDilleri,
            elemanlar, elemanEkle
        };



    }
};
</script>
<style>
  /* Ana arka plan rengi */
body {
  background-color: #f3f3f3;
  margin: 0;
  font-family: Arial, sans-serif;
}

/* Eleman kartları */
.eleman-karti {
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 20px;
  margin: 20px 0;
  background-color: #fff;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease-in-out;
}

.eleman-karti:hover {
  transform: translateY(-5px);
}

/* Başlık stilleri */
.eleman-karti h3 {
  margin-bottom: 10px;
  color: #333;
  font-size: 1.5rem;
}

/* Paragraf stilleri */
.eleman-karti p {
  margin-bottom: 5px;
  color: #555;
}

/* Giriş alanları */
input[type="text"],
input[type="number"],
button {
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 1rem;
}

/* Ekle butonu */
button {
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
  font-size: 1rem;
}

button:hover {
  background-color: #45a049;
}


</style>