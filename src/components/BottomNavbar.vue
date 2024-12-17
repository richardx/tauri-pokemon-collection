<template>
  <nav
    class="fixed bottom-0 left-0 w-full bg-white dark:bg-gray-800 shadow-md md:hidden"
  >
    <div class="flex justify-around">
      <!-- Collection -->
      <router-link
        to="/MyCollection"
        class="flex flex-col items-center justify-center py-2"
        active-class="text-blue-500 dark:text-blue-300"
      >
        <Squares2X2Icon class="h-8 w-8 mb-1 text-gray-600 dark:text-white" />
        <span class="text-lg text-gray-600 dark:text-white">Collection</span>
      </router-link>

      <!-- Wishlist -->
      <router-link
        to="/wishlist"
        class="flex flex-col items-center justify-center py-2"
        active-class="text-blue-500 dark:text-blue-300"
      >
        <HeartIcon class="h-8 w-8 mb-1 text-gray-600 dark:text-white" />
        <span class="text-lg text-gray-600 dark:text-white">Wishlist</span>
      </router-link>

      <!-- Scan -->
      <router-link
        to="/scan"
        class="flex flex-col items-center justify-center py-2"
        active-class="text-blue-500 dark:text-blue-300"
      >
        <CameraIcon class="h-8 w-8 mb-1 text-gray-600 dark:text-white" />
        <span class="text-lg text-gray-600 dark:text-white">Scan</span>
      </router-link>

      <!-- Sets -->
      <router-link
        to="/sets"
        class="flex flex-col items-center justify-center py-2"
        active-class="text-blue-500 dark:text-blue-300"
      >
        <BookOpenIcon class="h-8 w-8 mb-1 text-gray-600 dark:text-white" />
        <span class="text-lg text-gray-600 dark:text-white">Sets</span>
      </router-link>

      <!-- Profile -->
      <router-link
        to="/profile"
        class="flex flex-col items-center justify-center py-2"
        active-class="text-blue-500 dark:text-blue-300"
      >
        <UserIcon class="h-8 w-8 mb-1 text-gray-600 dark:text-white" />
        <span class="text-lg text-gray-600 dark:text-white">Profile</span>
      </router-link>
    </div>
  </nav>
</template>

<script setup>
  import {
    BookOpenIcon,
    CameraIcon,
    HeartIcon,
    Squares2X2Icon,
    UserIcon,
  } from '@heroicons/vue/24/outline';
</script>
