<template>
    <MainLayout>
        <div class="pt-[90px] 2xl:pl-[195px] lg:pl-[160px] lg:pr-0 pr-2 w-[calc(100%-90px)] max-w-[1800px] 2xl:mx-auto">
            <!-- <div class="flex w-[calc(100vw-230px)]"> -->
            <div class="flex">
                <img class="max-w-[120px] rounded-full"
                    src="https://p3-passport.byteimg.com/img/user-avatar/8b29c46c806762d72e9cb19a43b490dd~100x100.image">
                <div class="ml-5 w-full">
                    <div class="text-[30px] font-bold truncate">
                        User name
                    </div>
                    <div class="text-[18px] truncate">User name</div>
                    <button v-if="true"
                        class="flex items-center rounded-md py-1.5 px-3.5 mt-3 text-[15px] font-semibold border hover:bg-gray-100">
                        <Icon class="mt-0.5 mr-1" name="mdi:pencil" size="18" />
                        <div>Edit profile</div>
                    </button>
                    <button v-else
                        class="flex items-center rounded-md py-1.5 px-8 mt-3 text-[15px] text-white font-semibold bg-[#F02C56]">
                        Follow
                    </button>
                </div>
            </div>

            <div class="flex items-center pt-4">
                <div class="mr-4" v-for="item in list" :key="item.label">
                    <span class="font-bold">{{ item.number }}</span>
                    <span class="text-gray-500 font-light text-[15px] pl-1.5">{{ item.label }}</span>
                </div>
            </div>

            <div class="pt-4 mr-4 text-gray-500 font-light text-[15px] pl-1.5 max-w[500px]">
                This is the bio section
            </div>

            <div class="w-full flex items-center pt-4 border-b">
                <div class="w-60 text-center py-2 text-[17px] font-semibold border-b-2 border-b-black">Videos</div>
                <div class="w-60 text-gray-500 text-center py-2 text-[17px] font-semibold">
                    <Icon class="mb-0.5" name="material-symbols:lock-open" />
                    Liked
                </div>
            </div>

            <div class="mt-4 grid 2xl:grid-cols-6 xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 grid-cols-2 gap-3">
                <PostUser v-for="item in 30" :key="item" />
            </div>
        </div>
    </MainLayout>
</template>

<script setup lang="ts">
import MainLayout from '~/layouts/MainLayout.vue';


const list = [
    { number: '12K', label: 'Following' },
    { number: '34K', label: 'Followers' },
    { number: '56K', label: 'Likes' },
]
</script> 