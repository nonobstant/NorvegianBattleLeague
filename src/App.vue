<template>
  <div class="bg-gray-200 dark:bg-gray-900 dark:text-white min-h-screen text-center pt-5 transition duration-700 ease-in-out">
    <!-- <svg v-if='theme ==="light"'  @click="themeDark" class="w-10 h-10 inline cursor-crosshair p-2 hover:text-white hover:bg-black rounded-lg" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
     <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
    </svg>
    <svg v-else  @click="themeLight" class="w-10 h-10 inline cursor-crosshair p-2 hover:text-black hover:bg-white rounded-lg" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
     <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"></path>
    </svg> -->
    <span v-if='theme ==="light"'  @click="themeDark" class="text-3xl inline cursor-crosshair px-2 animate-bounce hover:text-red-400 rounded-full">♠</span>
    <span v-else  @click="themeLight" class="text-3xl inline cursor-crosshair px-2 animate-bounce hover:text-red-400 rounded-full">♦</span>
    <img class="mx-auto h-24 mt-7 mb-4 hover:animate-pulse" alt="Vue logo" src="./assets/danish.png" />
    <h1 class="text-3xl font-semibold font-serif" ><span class="text-teal-700">Norvegian Battle League</span></h1>
    <div class="p-2">
      <div class="border-t-4 border-red-400 p-4 max-w-2xl mx-auto mt-6 border-dashed">
        <p class="text-lg font-sans font-semibold text-gray-800 dark:text-gray-200">Welcome to the first Danish tournament !</p>

        <div class="uppercase max-w-2xl mx-auto mt-5 font-bold text-red-400 ">
          <a class="mx-2 hover:animate-pulse" href="">scoreboard</a> ▪
          <a class="mx-2 hover:animate-pulse" href="">rules</a> ▪
          <a class="mx-2 hover:animate-pulse" href="">matchs</a>
        </div>
      </div>
      <router-view class=""></router-view>
    </div>
    
    <!-- <h1 class="mt-16">Made with ❤ by nonobstant</h1> -->
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      theme : ""
    }
  },
  methods : {
    // Theme action
    themeLight() {
      document.documentElement.classList.remove("dark");
      localStorage.theme = "light";
      this.theme = "light";
    },
    themeDark() {
      document.documentElement.classList.add("dark");
      localStorage.theme = "dark";
      this.theme = "dark";
    },
  },
  mounted() {
    //theme setup
    if (
      localStorage.theme === "dark" ||
      (!("theme" in localStorage) &&
        window.matchMedia("(prefers-color-scheme: dark)").matches)
    ) {
      document.documentElement.classList.add("dark");
      this.theme = "dark";
    } else {
      document.documentElement.classList.remove("dark");
      this.theme = "light";
    }
  }
}
</script>

<style>
</style>
