<script setup>
import { ref } from 'vue';

const headtext = "This is a heading line text."
const image = "https://images.unsplash.com/photo-1459259191495-52eccde892c7?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D";
const text = "I love riding motorcycle anywhere on any given day. I have three different types of motorcycle in my garage at home. My first bike is a 2013 Yamaha underbone bike. It has two main colours, red and black.";
const width = 900;

const redText = "text-red-500"

const displayTitle = ref(true);
const displayImage = ref(true);
const displayText = false;

const activeCountry = ref('India');

  function setActiveCountry(){
    const userInput = prompt('Write Country Name');
    activeCountry.value = userInput;
  }

  function setBhutan (){
    activeCountry.value = 'Bhutan';
  }

  const showItems = true;

  const showCart = ref(false);

const titlecolor = 'green';
</script>



<template>
  <div>
    <h1 v-if="displayTitle" type="text/tailwindcss" class="text-left text-5xl pb-8">{{ headtext }}</h1>
    <img  v-show="displayImage" :width="width" :src="image"  alt="">
    <p v-show="displayText" class="pt-6 text-left mr-30" :class="redText">
      {{ text }}
    </p>
    <button @click="displayTitle = !displayTitle" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">Toggle Title</button>
    <button @click="displayImage = !displayImage" class="bg-blue-500 hover:bg-blue-700 text-white font-bold mt-10">Toggle Image</button>

  </div>

  <div>
    <!-- <p v-if="titlecolor == 'green'" class="text-green-500 text-2xl">I love Green color.</p>
    <p v-else-if="titlecolor == 'red'" class="text-red-500 text-2xl">I love Red color.</p>
    <p v-else-if="titlecolor == 'blue'" class="text-blue-400 text-2xl">I love Blue color.</p>
    <p v-else class="text-yellow-400 text-2xl">I love yellow color.</p> -->

    <!-- <p v-show="titlecolor == 'green'" class="text-green-500 text-2xl">I love Green color.</p>
    <p v-show="titlecolor == 'red'" class="text-red-500 text-2xl">I love Red color.</p>
    <p v-show="titlecolor == 'blue'" class="text-blue-400 text-2xl">I love Blue color.</p> -->
    <!-- <p v-else class="text-yellow-400 text-2xl">I love yellow color.</p> -->

  </div>

  <div>
    <h1 class="text-5xl my-10">Country Information -- {{ activeCountry }}</h1>
    <ul>
      <li class="p-5 text-left"  v-show="activeCountry == 'Bangladesh'">
    <h2><strong>Bangladesh</strong></h2>
    <p><strong>Capital:</strong>Dhaka</p>
    <p><strong>Population:</strong>200000000</p>
    <p><strong>Area:</strong>14570</p>
      </li>

      <li class="p-5 text-left" v-show="activeCountry == 'India'">
    <h2><strong>India</strong></h2>
    <p><strong>Capital:</strong>Dilhi</p>
    <p><strong>Population:</strong>200000000</p>
    <p><strong>Area:</strong>14570</p>
      </li>

      <li class="p-5 text-left" v-show="activeCountry == 'Nepal'">
    <h2><strong>Nepal</strong></h2>
    <p><strong>Capital:</strong>Katmondu</p>
    <p><strong>Population:</strong>200000000</p>
    <p><strong>Area:</strong>14570</p>
      </li>

      <li class="p-5 text-left" v-show="activeCountry == 'Bhutan'">
    <h2><strong>Bhutan</strong></h2>
    <p><strong>Capital:</strong>Thimpu</p>
    <p><strong>Population:</strong>200000000</p>
    <p><strong>Area:</strong>14570</p>
      </li>
    </ul>
  </div>

  <div>
    <button @click="setActiveCountry()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">Set Active Country</button>
  </div>

  <div>
    <button @click="activeCountry='Bangladesh'" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">Bangladesh</button>
    <button @click="activeCountry='India'" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">India</button>
    <button @click="activeCountry='Nepal'" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">Nepal</button>
    <button @click="setBhutan()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold  mt-10 mx-10">Bhutan</button>
  </div>

  <template class="text-left mt-7" v-if="showItems">
    <h3  class="text-left mt-7">1st Iteams</h3>
    <h3 class="text-left mt-7">2nd Iteams</h3>
    <h3 class="text-left mt-7">3rd Iteams</h3>
  </template>




  <div class="relative z-10" aria-labelledby="slide-over-title" role="dialog" aria-modal="true">
  <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity">
    <button @click="showCart=true" class="bg-blue-500 hover:bg-blue-700 font-bold text-white py-2 my-20">Display Shopping Cart</button>
  </div>


      <div v-show="showCart" class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10">
        <div class="pointer-events-auto w-screen max-w-md">
          <div class="flex h-full flex-col overflow-y-scroll bg-white shadow-xl">
            <div class="flex-1 overflow-y-auto px-4 py-6 sm:px-6">
              <div class="flex items-start justify-between">
                <h2 class="text-lg font-medium text-gray-900" id="slide-over-title">Shopping cart</h2>
                <div class="ml-3 flex h-7 items-center">
                  <button @click="showCart=false" type="button" class="relative -m-2 p-2 text-gray-400 hover:text-gray-500">
                    <span class="absolute -inset-0.5"></span>
                    <span class="sr-only">Close panel</span>
                    <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                    </svg>
                  </button>
                </div>
              </div>

              <div class="mt-8">
                <div class="flow-root">
                  <ul role="list" class="-my-6 divide-y divide-gray-200">
                    <li class="flex py-6">
                      <div class="h-24 w-24 flex-shrink-0 overflow-hidden rounded-md border border-gray-200">
                        <img src="https://tailwindui.com/img/ecommerce-images/shopping-cart-page-04-product-01.jpg" alt="Salmon orange fabric pouch with match zipper, gray zipper pull, and adjustable hip belt." class="h-full w-full object-cover object-center">
                      </div>

                      <div class="ml-4 flex flex-1 flex-col">
                        <div>
                          <div class="flex justify-between text-base font-medium text-gray-900">
                            <h3>
                              <a href="#">Throwback Hip Bag</a>
                            </h3>
                            <p class="ml-4">$90.00</p>
                          </div>
                          <p class="mt-1 text-sm text-gray-500">Salmon</p>
                        </div>
                        <div class="flex flex-1 items-end justify-between text-sm">
                          <p class="text-gray-500">Qty 1</p>

                          <div class="flex">
                            <button type="button" class="font-medium text-indigo-600 hover:text-indigo-500">Remove</button>
                          </div>
                        </div>
                      </div>
                    </li>
                    <li class="flex py-6">
                      <div class="h-24 w-24 flex-shrink-0 overflow-hidden rounded-md border border-gray-200">
                        <img src="https://tailwindui.com/img/ecommerce-images/shopping-cart-page-04-product-02.jpg" alt="Front of satchel with blue canvas body, black straps and handle, drawstring top, and front zipper pouch." class="h-full w-full object-cover object-center">
                      </div>

                      <div class="ml-4 flex flex-1 flex-col">
                        <div>
                          <div class="flex justify-between text-base font-medium text-gray-900">
                            <h3>
                              <a href="#">Medium Stuff Satchel</a>
                            </h3>
                            <p class="ml-4">$32.00</p>
                          </div>
                          <p class="mt-1 text-sm text-gray-500">Blue</p>
                        </div>
                        <div class="flex flex-1 items-end justify-between text-sm">
                          <p class="text-gray-500">Qty 1</p>

                          <div class="flex">
                            <button type="button" class="font-medium text-indigo-600 hover:text-indigo-500">Remove</button>
                          </div>
                        </div>
                      </div>
                    </li>

                    <!-- More products... -->
                  </ul>
                </div>
              </div>
            </div>

            <div class="border-t border-gray-200 px-4 py-6 sm:px-6">
              <div class="flex justify-between text-base font-medium text-gray-900">
                <p>Subtotal</p>
                <p>$262.00</p>
              </div>
              <p class="mt-0.5 text-sm text-gray-500">Shipping and taxes calculated at checkout.</p>
              <div class="mt-6">
                <a href="#" class="flex items-center justify-center rounded-md border border-transparent bg-indigo-600 px-6 py-3 text-base font-medium text-white shadow-sm hover:bg-indigo-700">Checkout</a>
              </div>
              <div class="mt-6 flex justify-center text-center text-sm text-gray-500">
                <p>
                  or
                  <button type="button" class="font-medium text-indigo-600 hover:text-indigo-500">
                    Continue Shopping
                    <span aria-hidden="true"> &rarr;</span>
                  </button>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>

</div>


</template>




<style scoped>

</style>
