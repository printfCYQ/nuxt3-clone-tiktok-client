<template>
    <div id="TopNav" class="fixed bg-white z-30 flex items-center w-full border-b h-[61px]">
        <div :class="route.fullPath === '/' ? 'max-w-[1150px]' : ''"
            class="flex items-center justify-center w-full px-6 mx-auto">

            <!-- logo -->
            <div :class="route.fullPath === '/' ? 'w-[80%]' : 'lg:w-[20%] w-[70%]'">
                <NuxtLink to="/">
                    <img width="115" src="~/assets/images/tiktok-logo.png" alt="">
                </NuxtLink>
            </div>

            <!-- search input -->
            <div class="hidden md:flex items-center bg-[#F1F1F2] p-1 rounded-full max-w-[380px] w-full">
                <input class="w-full pl-3 my-2 bg-transparent placeholder-[#838383] text-[15px] focus:outline-none"
                    placeholder="Search accounts" type="text">
                <div class="px-3 py-1 flex items-center border-l border-l-gray-300">
                    <Icon name="ic:baseline-search" color="#A1A2A7" size="27" />
                </div>
            </div>

            <!-- upload & account -->
            <div class="flex items-center justify-end gap-3 min-w-[275px] max-w-[320px] w-full">
                <button class="flex items-center border rounded-sm px-3 py-[6px] hover:color-gray-100">
                    <Icon name="mdi-plus" color="#000000" size="22" />
                    <span class="px-2 font-medium text-[15px]">Upload</span>
                </button>

                <div v-if="false" class="flex items-center">
                    <button class="flex items-center bg-[#F02C56] text-white border rounded-md px-3 py-[6px]">
                        <span class="mx-4 font-medium text-[15px]">Login</span>
                    </button>
                    <Icon name="mdi-dots-vertical" color="#161724" size="25" />
                </div>

                <div class="flex items-center">
                    <Icon class="ml-1 mr-4" name="carbon:send-alt" color="#161724" size="30" />
                    <Icon class="mr-5" name="bx:message-detail" color="#161724" size="27" />
                    <div class="relative">
                        <button class="mt-1">
                            <img class="rounded-full" width="33" @click="showMenu = !showMenu"
                                src="https://p3-passport.byteimg.com/img/user-avatar/8b29c46c806762d72e9cb19a43b490dd~100x100.image">
                        </button>

                        <div v-if="showMenu" id="PopMenu"
                            class="absolute bg-white rounded-lg py-1.5 w-[200px] shadow-xl border top-[43px] -right-2">
                            <NuxtLink @click="showMenu = false"
                                class="flex items-center justify-start py-3 px-2 hover:bg-gray-100 cursor-pointer">
                                <Icon name="ph:user" color="" size="20" />
                                <span class="pl-2 font-semibold text-sm">Profile</span>
                            </NuxtLink>
                            <div
                                class="flex items-center justify-start py-3 px-1.5 border-t hover:bg-gray-100 cursor-pointer">
                                <Icon name="ic:outline-login" color="" size="20" />
                                <span class="pl-2 font-semibold text-sm">Log out</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const route = useRoute();

const showMenu = ref<boolean>(false)
</script>
 