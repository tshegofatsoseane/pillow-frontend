<template>
    <nav :class="{ 'fixed text-white bg-white bg-opacity-30 backdrop-blur-lg shadow-md': isScrolled, 'text-white': isScrolled, 'py-1': !isScrolled, 'py-1': isScrolled }" class="fixed  text-white top-0 w-full font-bold z-20" :style="{ transition: isScrolled ? 'background-color 2s, color 0.5s' : 'none' }">
        <div class="container  mx-auto px-4 flex justify-between items-center" :class="{ 'my-1'  :isScrolled,  'my-6'  :!isScrolled}">
            <!-- Logo -->
 <div class="flex items-center ml-6">
  <img src="@/assets/logo.png" alt="Pillow Logo" class="h-8 w-auto mr-2">
  <div class="text-2xl font-bold border-white rounded-full " :class="{ 'text-indigo-500': isScrolled }">Pillow</div>
</div>


            <!-- Burger Menu -->
            <button @click="toggleMenu" class="block lg:hidden text-gray-400 focus:outline-none" >
                <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
                </svg>
            </button>

            <!-- Navigation Links -->
            <div :class="{ 'hidden': !showMenu, 'lg:flex': showMenu }" class="lg:flex hover:border-white">
                <router-link to="/" class="px-4 py-4 transition duration-700 ease-in-out hover:text-blue-500 hover:border-blue-500" :class="{ 'border-b-2 border-blue-500': $route.path === '/', 'text-black border-indigo-500': isScrolled }">Home</router-link>
                <router-link :to="{ name: 'innovation' }" class="px-4 py-4 transition duration-300 ease-in-out hover:text-blue-500 hover:border-blue-500" :class="{ 'border-b-2 border-blue-500': $route.name === 'innovation', 'text-black border-indigo-400': isScrolled }">For Landlords</router-link>
            </div>

<!-- Action Buttons -->
<div class="mr-12 flex items-center space-x-4"> <!-- Modified this line -->
    <router-link :to="{ name: 'innovation' }" 
             class="border font-semibold py-2 px-6 rounded transition duration-300 ease-in-out hover:text-indigo-500 hover:border-blue-500"
             :class="{ 'border-white': !isScrolled, 
                        'border-indigo-700': isScrolled,
                        'text-white': !isScrolled,
                        'text-indigo-500': isScrolled }">
    Login
</router-link>
<router-link :to="{ name: 'signup' }"  class="bg-gradient-to-r from-indigo-600/90 to-pink-800/50 hover:bg-indigo-600/60 text-white font-semibold py-2 px-6 rounded transition duration-300 ease-in-out">Signup</router-link>
</div>


            
        </div>
    </nav>
</template>

<script>
export default {
    name: 'Navbar',
    data() {
        return {
            showMenu: false,
            isScrolled: false
        }
    },
    mounted() {
        window.addEventListener('scroll', this.handleScroll);
    },
    beforeDestroy() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
        toggleMenu() {
            this.showMenu = !this.showMenu;
        },
        handleScroll() {
            this.isScrolled = window.scrollY > 0;
        }
    }
}
</script>

<style>
/* Add any styles you need */
</style>
