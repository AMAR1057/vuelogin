<script setup>
import { useRouter } from "vue-router";
import useAuth from "../composable/useAuth";
const { isAuthenticated, logout } = useAuth();
const router = useRouter();
const loggingOut = () => {
  logout();
  router.push("/");
};
</script>

<template>
  <div class="text-pink-200 bg-pink-500">
    <div class="container flex items-center justify-between mx-auto">
      <h1 class="text-3xl font-thin tracking-tighter">
        Vue<span class="font-normal">RealAuth</span>
      </h1>
      <nav>
        <ul class="flex space-x-4">
          <router-link to="/">
            <li
              class="px-4 py-8  hover:cursor-pointer hover:bg-pink-300 hover:text-pink-200"
            >
              Home
            </li>
          </router-link>
          <router-link :to="{ name: 'About' }">
            <li
              class="px-4 py-8  hover:cursor-pointer hover:bg-pink-300 hover:text-pink-200"
            >
              About
            </li>
          </router-link>
          <router-link
            v-if="!isAuthenticated"
            :to="{ path: '/login', name: 'Login' }"
          >
            <li
              class="px-4 py-8  hover:cursor-pointer hover:bg-pink-300 hover:text-pink-200"
            >
              Login
            </li>
          </router-link>
          <div v-else class="flex">
            <router-link :to="{ name: 'Secret' }">
              <li
                class="px-4 py-8  hover:cursor-pointer hover:bg-pink-300 hover:text-pink-200"
              >
                Secret
              </li>
            </router-link>
             <button @click="loggingOut">
              <li
                class="px-4 py-8  hover:cursor-pointer hover:bg-pink-300 hover:text-pink-200"
              >
                Logout
              </li>
            </button>
          </div>
        </ul>
      </nav>
    </div>
  </div>
</template>