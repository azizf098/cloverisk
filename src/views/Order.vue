<template>
  <div class="pt-20 ">
      <div class="container mx-auto px-4">
        <div class="message text-center">
          <h1 class="text-3xl font-bold pt-10">Terimakasih Telah Memesan</h1>
          <br>
          <!-- component -->
          <p>Kode Pemesanan : {{ getOrder.code }}</p>
          <p class="italic">
            Terimakasih atas kepercayaan Tn./Ny. {{ getOrder.user.name }} 
          </p>

        </div>
        </div>
        </div>
        <section class="relative py-18 bg-blueGray-100">
<div class="w-full mb-12 px-4">
<div class="relative flex flex-col min-w-0 break-words w-full mb-6 shadow-lg rounded 
 text-white">
  <div class="rounded-t mb-0 px-4 py-3 border-0">
    <div class="flex flex-wrap items-center">
      <div class="relative w-full px-4 max-w-full flex-grow flex-1 ">
        <h3 class="font-bold text-lg underline text-black px-6  align-middle border border-white py-4 uppercase  text-center bg-grey-600 text-purple-900 border-grey-700">Rincian Pesanan</h3>
      </div>
    </div>
  </div>
  <div class="block w-full overflow-x-auto ">
    <div class="container mx-auto px-6">
        <div class="mx-10 mt-10">
          <div class="grid grid-cols-2">
            <div>
              <dl
                class="max-w-md text-gray-900 divide-y divide-gray-200 dark:text-white dark:divide-gray-700"
              >
                <div class="flex flex-col pb-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Kode Pemesanan : 
                  </dt>
                  <dd class="text-lg font-semibold">{{ getOrder.code }}</dd>
                </div>
                <div class="flex flex-col pb-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Nama : 
                  </dt>
                  <dd class="text-lg font-semibold">{{ getOrder.user.name  }}</dd>
                </div>
                <div class="flex flex-col pb-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                     Email : 
                  </dt>
                  <dd class="text-lg font-semibold">{{ getOrder.user.email }}</dd>
                </div>
                <div class="flex flex-col pt-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Nomor Telpon :
                  </dt>
                  <dd class="text-lg font-semibold">
                    {{  getOrder.shipping_address.phone }}
                  </dd>
                </div>
                <div class="flex flex-col py-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Alamat Rumah : 
                  </dt>
                  <dd class="text-lg font-semibold">
                    {{ getOrder.shipping_address.address }}, {{  getOrder.shipping_address.city }}, {{  getOrder.shipping_address.state }}, {{  getOrder.shipping_address.country }}, {{  getOrder.shipping_address.postal_code }}
                  </dd>
                </div>
              </dl>
            </div>
            <div>
              <dl
                class="max-w-md text-gray-900 divide-y divide-gray-200 dark:text-white dark:divide-gray-700"
              >
                <div class="flex flex-col pb-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Metode Pembayaran : 
                  </dt>
                  <dd class="text-lg font-semibold">{{ getOrder.orders[0].payment_type }}</dd>
                </div>
                <div class="flex flex-col pb-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Metode Pengiriman : 
                  </dt>
                  <dd class="text-lg font-semibold">{{ getOrder.orders[0].delivery_type }}</dd>
                </div>
                <div class="flex flex-col pt-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Total Harga Barang :
                  </dt>
                  <dd class="text-lg font-semibold">
                    {{  getOrder.orders[0].grand_total }}
                  </dd>
                </div>
                <div class="flex flex-col pt-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Tanggal Beli :
                  </dt>
                  <dd class="text-lg font-semibold">
                    {{  getOrder.date }}
                  </dd>
                </div>
                <div class="flex flex-col py-3">
                  <dt class="mb-1 text-gray-500 md:text-lg dark:text-gray-400">
                    Alamat Tagihan : 
                  </dt>
                  <dd class="text-lg font-semibold">
                    {{ getOrder.shipping_address.address }}, {{  getOrder.shipping_address.city }}, {{  getOrder.shipping_address.state }}, {{  getOrder.shipping_address.country }}, {{  getOrder.shipping_address.postal_code }}
                  </dd>
                </div>
              </dl>
            </div>
          </div>
        </div>
        {{ orderData }}
      </div>
    </div>
    </div>
    <table
          class="w-full text-sm text-left text-gray-500 dark:text-gray-400"
        >
          <thead
            class="text-xs text-gray-700 uppercase bg-amber-100 dark:bg-gray-700 dark:text-gray-400"
          >
            <tr>
              <th scope="col" class="px-6 py-3">No.</th>
              <th scope="col" class="px-6 py-3">Produk</th>
              <th scope="col" class="px-6 py-3">Jumlah</th>
              <th scope="col" class="px-6 py-3">Harga</th>
            </tr>
          </thead>
          <tbody>
            <tr class="bg-amber-50 border-b dark:bg-gray-800 dark:border-gray-700" v-for="(order, index) in getOrder.orders[0].products.data">
              <th
                scope="row"
                class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white"
              >
              {{ index + 1 }}
              </th>
              <td class="px-6 py-4">{{ order.name }}</td>
              <td class="px-6 py-4">{{ order.quantity }}</td>
              <td class="px-6 py-4">{{ order.total }}</td>
            </tr>
          </tbody>
        </table>
        <div class="mt-6 border-t border-b py-2">
            <div class="flex items-center justify-between">
              <p class="text-sm font-medium text-gray-900">Total Belanja</p>
              <p class="font-semibold text-gray-900">Rp. {{ getOrder.grand_total }}</p>
            </div>
          </div>
          <div class="mt-6 flex items-center justify-between">
            <p class="text-sm font-medium text-gray-900">Total Harga : </p>
            <p class="text-2xl font-semibold text-gray-900">
              Rp. {{ getOrder.grand_total }}
            </p>
          </div>
          <br>
          <hr> 
          <div class="py-10 text-center">
                <a href="/produk" class="px-12 bg-indigo-600 hover:bg-indigo-500 text-white font-semibold py-3">
                    Kembali 
               </a>
            </div>
    </div>
    </section>
  </template>
  
  <script>
  import { mapGetters } from 'vuex';
  export default {
    props: ['orderCode'],
    computed: {
      ...mapGetters('order', ['getOrder']),
    },
    created() {
      this.$store.dispatch('order/fetchOrderData', this.orderCode);
    },
  };
  </script>