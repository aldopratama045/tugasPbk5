<template>
  <q-layout view="hHh lpR fFf">
    <!-- Navbar -->
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          Toko Kikss
        </q-toolbar-title>
        <q-btn dense flat round icon="shopping_cart" />
      </q-toolbar>
    </q-header>

    <!-- Main Content -->
    <q-page-container>
      <q-page padding class="q-pa-md">
        <!-- Carousel -->
        <q-carousel
          v-model="slide"
          arrows
          infinite
          animated
          control-color="black"
          swipeable
          transition-prev="slide-right"
          transition-next="slide-left"
          height="550px"
          class="bg-dark text-white shadow-2 rounded-borders"
        >
          <q-carousel-slide v-for="(image, index) in carouselImages" :key="index" :name="index" :img-src="image">
          </q-carousel-slide>
        </q-carousel>

        <!-- Cards -->
        <div class="q-mt-xl row justify-center">
          <q-card v-for="product in products" :key="product.name" class="my-card q-mb-xl q-pa-md col-xs-12 col-sm-6 col-md-4 col-lg-3">
            <q-img :src="product.image" :alt="product.name" class="my-card-img">
              <q-badge color="red" floating>{{ product.discount }}Flash Sale</q-badge>
            </q-img>
            <q-card-section>
              <div class="text-h6 text-center">{{ product.name }}</div>
              <div class="text-subtitle1 text-center">{{ product.price }}</div>
            </q-card-section>
            <q-card-actions align="center">
              <q-btn flat label="Add to Cart" color="primary" />
            </q-card-actions>
          </q-card>
        </div>
      </q-page>
    </q-page-container>

    <!-- Footer -->
    <q-footer class="bg-blue-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          &copy; 2024 Toko Kikss
        </q-toolbar-title>
        <div>
          <q-btn flat round icon="facebook" />
          <q-btn flat round icon="twitter" />
          <q-btn flat round icon="instagram" />
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const slide = ref(0);
    const carouselImages = [
      'https://i.pinimg.com/564x/3a/35/7b/3a357b6feced2f3c79043d7306222cf0.jpg',  // Ganti dengan URL gambar Anda
      'https://i.pinimg.com/564x/ac/9b/c1/ac9bc1e7593290bbb6bfbd0ea4b189e9.jpg',
      'https://i.pinimg.com/736x/cb/0b/f8/cb0bf82afc60f4b8c9211c5f0df0c281.jpg',
      'https://i.pinimg.com/564x/9a/fd/f8/9afdf85ce320f90b6abc208fecdfe9cf.jpg'
    ];
    const products = [
      { name: 'kemeja 1', price: 'Rp. 150K', image: 'https://i.pinimg.com/564x/3a/35/7b/3a357b6feced2f3c79043d7306222cf0.jpg'},  // Ganti dengan URL gambar Anda
      { name: 'Kemeja 2', price: 'Rp. 170K', image: 'https://i.pinimg.com/564x/ac/9b/c1/ac9bc1e7593290bbb6bfbd0ea4b189e9.jpg'},
      { name: 'Kemeja 3', price: 'Rp. 185K', image: 'https://i.pinimg.com/736x/cb/0b/f8/cb0bf82afc60f4b8c9211c5f0df0c281.jpg'},
      { name: 'Kemeja 4', price: 'Rp. 190K', image: 'https://i.pinimg.com/564x/9a/fd/f8/9afdf85ce320f90b6abc208fecdfe9cf.jpg'}
    ];

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value;
    };

    return {
      leftDrawerOpen,
      toggleLeftDrawer,
      slide,
      carouselImages,
      products
    };
  }
};
</script>

<style>
.my-card {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}
.my-card-img {
  border-radius: 10px 10px 0 0;
  height: 200px;
}
.rounded-borders {
  border-radius: 10px;
}
.q-footer {
  border-top: 1px solid #003285;
}
</style>
