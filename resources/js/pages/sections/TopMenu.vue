<template>
    <nav id="header" class="fixed w-full z-30 top-0 text-white"
         :class="{'bg-white': fixedHeader || menuVisible, shadow: fixedHeader || menuVisible}">

        <div class="px-4 w-full flex flex-wrap items-center justify-between mt-0 py-2">

            <div class="flex items-center w-full xs:w-auto">
                <a class="text-white no-underline hover:no-underline mr-4 xs:mr-0 font-bold text-2xl lg:text-4xl flex items-center"
                   href="/"
                   :class="{'text-gray-50': !fixedHeader, 'text-gray-800': fixedHeader || menuVisible}">
                    <webp class="mr-2" :src="'/img/logos/'+game+'.png'" :alt="$t(game)" width="250" height="35" :lazy="false"></webp>
                    <span class="hidden sm:inline">Storyline</span>
                </a>

                <a :href="this.appUrl"
                   class="inline-block xs:hidden ml-auto text-center rounded-lg border border-transparent bg-blue-600 px-4 py-2 leading-none font-medium text-white hover:bg-blue-500 focus:outline-none focus:border-blue-700 focus:shadow-outline-blue transition ease-in-out duration-150">
                    App
                </a>

                <!--
                <div class="block xs:hidden ml-auto pr-4">
                    <button id="nav-toggle" class="flex items-center p-1"
                            :class="{'text-gray-50 hover:text-gray-600': !fixedHeader, 'text-gray-900 hover:text-gray-500': fixedHeader || menuVisible}"
                            @click="toggleMenu">
                        <svg class="fill-current h-6 w-6" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title>
                            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/>
                        </svg>
                    </button>
                </div>
                -->
            </div>

            <div
                class="w-full flex-grow flex xs:flex flex-col-reverse xs:flex-row items-center xs:w-auto mt-2 xs:mt-0 xs:bg-transparent text-black p-4 pb-0 xs:p-0 z-20"
                :class="{hidden: !menuVisible, 'bg-gray-50': !fixedHeader, 'bg-white': fixedHeader || menuVisible}">
                <ul class="list-reset xs:flex justify-end flex-1 items-center mt-2 xs:mt-0">
                    <li class="xs:mr-1 pr-3 md:pr-5 py-2 xs:hidden sm:!inline-block text-center">
                        <a href="/#faq" class="hover:underline"
                           :class="{'text-gray-50': !fixedHeader, 'text-gray-800': fixedHeader || menuVisible}">FAQ</a>
                    </li>
                    <li class="xs:mr-1 pr-3 md:pr-5 py-2 xs:hidden sm:!inline-block text-center">
                        <a href="/#pricing" class="hover:underline"
                           :class="{'text-gray-50': !fixedHeader, 'text-gray-800': fixedHeader || menuVisible}">Contribute</a>
                    </li>
                    <!--
                    <li class="xs:mr-1 xs:hidden sm:!inline-block text-center">
                        <email-me
                            class="w-full hover:underline xs:w-auto xs:my-0 text-center inline-block no-underline hover:text-underline py-2 px-4"
                            :class="{'text-gray-50': !fixedHeader, 'text-gray-800': fixedHeader || menuVisible}">
                            Contact
                        </email-me>
                    </li>
                    -->
                </ul>
                <a :href="this.appUrl"
                   class="inline-block text-center rounded-lg border border-transparent bg-blue-600 px-4 py-2 leading-none font-medium text-white hover:bg-blue-500 focus:outline-none focus:border-blue-700 focus:shadow-outline-blue transition ease-in-out duration-150">
                    App
                </a>
            </div>
        </div>

        <hr class="border-b border-gray-50 opacity-25 my-0 py-0"/>
    </nav>
</template>

<script>
export default {
    props: {},
    data() {
        return {
            game: process.env.MIX_MAIN_GAME,
            appUrl: process.env.MIX_APP_URL,
            menuVisible: false,
            fixedHeader: false
        }
    },
    mounted() {
        document.addEventListener('scroll', () => {
            this.fixedHeader = window.scrollY > 10;
        });
    },
    methods: {
        toggleMenu() {
            this.menuVisible = !this.menuVisible;
        }
    }
}
</script>
