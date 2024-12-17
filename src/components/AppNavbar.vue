<template>
  <nav class="bg-white dark:bg-gray-900 shadow-md">
    <div class="w-full px-4">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <router-link to="/" class="flex items-center">
          <img src="@/assets/pokeball.png" alt="Logo" class="h-8 w-8 mr-2" />
          <span class="text-2xl font-bold text-gray-800 dark:text-white">
            Pokémon Collection
          </span>
        </router-link>

        <!-- Desktop Navigation Links -->
        <div class="hidden md:flex items-center space-x-8">
          <router-link
            to="/MyCollection"
            class="text-gray-600 hover:text-blue-500 dark:text-gray-300 dark:hover:text-blue-300"
            active-class="font-semibold"
          >
            Collection
          </router-link>
          <router-link
            to="/wishlist"
            class="text-gray-600 hover:text-blue-500 dark:text-gray-300 dark:hover:text-blue-300"
            active-class="font-semibold"
          >
            Wishlist
          </router-link>
          <router-link
            to="/sets"
            class="text-gray-600 hover:text-blue-500 dark:text-gray-300 dark:hover:text-blue-300"
            active-class="font-semibold"
          >
            Sets
          </router-link>
          <router-link
            to="/profile"
            class="text-gray-600 hover:text-blue-500 dark:text-gray-300 dark:hover:text-blue-300"
            active-class="font-semibold"
          >
            Profile
          </router-link>
          <router-link
            to="/scan"
            class="text-gray-600 hover:text-blue-500 dark:text-gray-300 dark:hover:text-blue-300"
            active-class="font-semibold"
          >
            Scan
          </router-link>

          <!-- Dark Mode Toggle -->
          <button @click="toggleDarkMode" class="focus:outline-none">
            <span v-if="!isDarkMode">🌞</span>
            <span v-else>🌙</span>
          </button>
        </div>

        <!-- Mobile Dark Mode Toggle (hidden on md and up) -->
        <div class="md:hidden flex items-center">
          <button @click="toggleDarkMode" class="focus:outline-none">
            <span v-if="!isDarkMode">🌞</span>
            <span v-else>🌙</span>
          </button>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
  import { auth } from '@/firebase';
  import { useUserStore } from '@/store';
  import { signOut } from 'firebase/auth';

  export default {
    name: 'AppNavbar',
    data() {
      return {
        isMenuOpen: false, // Tilstandsvariabel for mobile menu
      };
    },
    computed: {
      user() {
        const userStore = useUserStore();
        return userStore.user;
      },
      isDarkMode() {
        const userStore = useUserStore();
        return userStore.isDarkMode;
      },
    },
    methods: {
      toggleMenu() {
        this.isMenuOpen = !this.isMenuOpen;
      },
      toggleDarkMode() {
        const userStore = useUserStore();
        userStore.toggleDarkMode();
      },
      logout() {
        signOut(auth)
          .then(() => {
            const userStore = useUserStore();
            userStore.setUser(null);
            this.$router.push({ name: 'LoginUser' });
          })
          .catch((error) => {
            console.error('Logout fejlede:', error);
          });
      },
    },
  };
</script>
