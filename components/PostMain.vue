<template>
    <div id="PostMain" class="flex border-b py-6">
        <div class="cursor-pointer">
            <img class="rounded-full max-h-[60px]" width="60"
                src="https://p3-passport.byteimg.com/img/user-avatar/8b29c46c806762d72e9cb19a43b490dd~100x100.image">
        </div>
        <div class="pl-3 w-full px-4">
            <div class="flex items-center justify-between pb-0.5">
                <button>
                    <span class="font-bold hover:underline cursor-pointer">
                        User name
                    </span>
                    <span class="text-[13px] text-light text-gray-500 pl-1 cursor-pointer">
                        User name
                    </span>
                </button>

                <button
                    class="border text-[15px] px-[21px] py-0.5 border-[#E02C56] text-[#E02C56] hover:bg-[#ffeef2] font-semibold rounded-md">
                    Follow
                </button>
            </div>

            <div class="text-[15px] pb-0.5 break-words md:max-w-[400px] max-w-[300px]">
                This is some text
            </div>
            <div class="text-[14px] text-gray-500 pb-0.5">
                #fun #cool #Superwesome
            </div>
            <div class="text-[14px] pb-0.5 flex items-center font-semibold">
                <Icon name="mdi:music" color="" size="17" />
                <div class="px-1">original sound - AWESOME</div>
                <Icon name="mdi:heart" color="" size="20" />
            </div>

            <div class="mt-2.5 flex">
                <div
                    class="relative min-h-[480px] max-h-[580px] max-w-[260px] flex items-center bg-black rounded-xl cursor-pointer">
                    <video ref="video" loop muted class="rounded-xl object-cover mx-auto h-full" src="test.mp4"></video>
                    <img class="absolute right-2 bottom-14" width="90" src="~/assets/images/tiktok-logo-white.png" alt="">
                </div>

                <div class="relative mr-[75px]">
                    <div class="absolute bottom-0 pl-2">
                        <div class="pb-4 text-center">
                            <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                                <Icon name="mdi:heart" color="" size="25" />
                            </button>
                            <span class="text-xs text-gray-800 font-semibold">12</span>
                        </div>
                        <div class="pb-4 text-center">
                            <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                                <Icon name="bx:bxs-message-rounded-dots" color="" size="25" />
                            </button>
                            <span class="text-xs text-gray-800 font-semibold">34</span>
                        </div>
                        <div class="pb-4 text-center">
                            <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                                <Icon name="ri:share-forward-fill" color="" size="25" />
                            </button>
                            <span class="text-xs text-gray-800 font-semibold">56</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
const video = ref<HTMLVideoElement>()

onMounted(() => {
    (video.value as HTMLVideoElement).play()
})
</script>