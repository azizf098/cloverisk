<template>
  <div v-if="getProduk == false">
      <div class="h-screen bg-white">
          <div class="flex justify-center items-center h-full">
              <img class="h-16 w-16" src="https://icons8.com/preloaders/preloaders/1488/Iphone-spinner-2.gif" alt="">
          </div>
      </div>
  </div>
  <div v-else>
      <div class="mt-10 grid grid-cols-1 gap-1 sm:grid-cols-4 sm:gap-2 lg:mt-16">
          <!-- <div class="grid md:grid-cols-3 gap-8  mt-10 pl-5"></div> -->
      <div v-for="product in getProduk" :key="product.slug">
          <section class="bg-white py-12 text-gray-700 sm:py-16 lg:py-20">
              <div class="mx-auto max-w-screen-xl px-4 sm:px-6 lg:px-8">
                 
                      <article class="relative flex flex-col overflow-hidden rounded-lg border">
                          <div class="aspect-square overflow-hidden">
                              <img class="h-700 w-700 object-cover transition-all duration-300 group-hover:scale-125" style="margin-left: 6%;"
                                  src="https://th.bing.com/th/id/OIP.gy5ir7_Nb5DvWgr8IAbDtgHaFb?w=250&h=184&c=7&r=0&o=5&pid=1.7" alt="" />
                          </div>
                          <div class="absolute top-0 m-2 rounded-full bg-white">
                              <p
                                  class="rounded-full bg-emerald-500 p-1 text-[8px] font-bold uppercase tracking-wide text-white sm:py-1 sm:px-3">
                                  Sale</p>
                          </div>
                          <div class="my-4 mx-auto flex w-10/12 flex-col items-start justify-between">
                              <div class="mb-2 flex">
                                  <p class="mr-3 text-xl font-semibold">Rp.{{ product.base_price }}</p>
                              </div>
                              <h3 class="mb-2 text-2xl ">{{ product.name }}</h3>
                              <!-- <h3 class="mb-2 text-xl text-gray-400">Stok:{{ product.stock }}</h3> -->
                          </div>
                          <router-link :to="{ name: 'SingleProduk', params: { slug: product.slug } }">
                          <button
                              class="group mx-auto mb-2 flex h-10 w-10/12 items-stretch overflow-hidden rounded-md text-gray-600">
                              <div
                                  class="flex w-full items-center justify-center bg-gray-100 text-xs uppercase transition group-hover:bg-emerald-600 group-hover:text-white">
                                  Tambah</div>
                              <div
                                  class="flex items-center justify-center bg-gray-200 px-5 transition group-hover:bg-emerald-500 group-hover:text-white">
                                  +</div>
                          </button>
                      </router-link>
                      </article>
              </div>
          </section>
      </div>
  </div>
  </div>
</template>
<script>
import { mapGetters, mapActions } from 'vuex';

export default {
  computed: {
      ...mapGetters('product', ['getProduk']),
  },
  methods: {
      ...mapActions('product', ['fetchProduk']),
  },
  created() {
      this.fetchProduk();
  }
}
</script>