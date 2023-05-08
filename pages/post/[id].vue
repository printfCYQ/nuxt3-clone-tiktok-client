<template>
    <div id="PostPage"
        class="fixed lg:flex justify-between z-50 top-0 left-0 w-full h-full bg-black lg:overflow-hidden overflow-auto">

        <!-- left -->
        <div class="lg:w-[calc(100%-540px)] h-full relative">
            <NuxtLink class="absolute z-20 m-5 rounded-full bg-gray-700 p-1.5 hover:bg-gray-800">
                <Icon name="material-symbols:close" color="#ffffff" size="27" />
            </NuxtLink>
            <div v-if="true">
                <button
                    class="absolute z-20 right-4 top-4 flex items-center justify-center rounded-full bg-gray-700 p-1.5 hover:bg-gray-800"
                    :disabled="!isLoaded" @click="loopThroughPostUp">
                    <Icon name="mdi:chevron-up" color="#ffffff" size="30" />
                </button>
                <button
                    class="absolute z-20 right-4 top-20 flex items-center justify-center rounded-full bg-gray-700 p-1.5 hover:bg-gray-800"
                    :disabled="!isLoaded" @click="loopThroughPostDown">
                    <Icon name="mdi:chevron-down" color="#ffffff" size="30" />
                </button>
            </div>

            <img class="absolute top-[18px] left-[70px] rounded-full lg:mx-0 mx-auto" width="45"
                src="~/assets/images/tiktok-logo-small.png" alt="">

            <video v-if="true" class="absolute object-cover w-full my-auto z-[-1] h-screen" src="/test.mp4"></video>

            <div v-if="!isLoaded" class="flex items-center justify-center bg-black bg-opacity-70 h-screen lg:min-w-[480px]">
                <Icon class="animate-spin ml-1" name="mingcute:loading-fill" color="#ffffff" size="100" />
            </div>
            <div class="bg-black bg-opacity-70 lg:min-w-[480px]">
                <video v-if="true" ref="video" loop muted class="h-screen mx-auto" src="/test.mp4"></video>
            </div>
        </div>

        <!-- right -->
        <div id="InfoSection" v-if="true" class="lg:max-w-[550px] relative w-full h-full bg-white">
            <div class="py-7"></div>
            <div class="flex items-center justify-between px-8">
                <div class="flex items-center">
                    <NuxtLink href="/">
                        <img class="rounded-full lg:mx=0 mx-auto" width="40"
                            src="https://p3-passport.byteimg.com/img/user-avatar/8b29c46c806762d72e9cb19a43b490dd~100x100.image"
                            alt="">
                    </NuxtLink>

                    <div class="ml-3 pt-0.5">
                        <div class="text-[17px] font-semibold">
                            User name
                        </div>
                        <div class="text-[13px] -mt-5 font-light">
                            User name
                            <span class="relative -top-[2px] text-[30px] pr-0.5">.</span>
                            <span class="font-semibold">Date here</span>
                        </div>
                    </div>
                </div>
                <Icon v-if="true" @click="deletePost" class="cursor-pointer" name="material-symbols:delete-outline-sharp"
                    color="" size="25" />
            </div>

            <div class=" px-8 mt-4 text-sm"> This is the post text.</div>

            <div class="px-8 mt-4 text-sm font-semibold">
                <Icon name="mdi:music" color="" size="17" />
                original sound - User name
            </div>

            <div class="flex items-center px-8 mt-8">
                <div class="pb-4 text-center flex items-center">
                    <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                        <Icon name="mdi:heart" color="" size="25" />
                    </button>
                    <span class="text-xs pl-2 pr-4 text-gray-800 font-semibold">123</span>
                </div>

                <div class="pb-4 text-center flex items-center">
                    <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                        <Icon name="bx:bxs-message-rounded-dots" color="" size="25" />
                    </button>
                    <span class="text-xs pl-2 pr-4 text-gray-800 font-semibold">234</span>
                </div>

                <div class="pb-4 text-center flex items-center">
                    <button class="rounded-full bg-gray-200 p-2 cursor-pointer">
                        <Icon name="ri:share-forward-fill" color="" size="25" />
                    </button>
                    <span class="text-xs pl-2 pr-4 text-gray-800 font-semibold">456</span>
                </div>
            </div>

            <!-- 评论列表 -->
            <div id="Comments" class="bg-[#f8f8f8] z-0 w-full h-[calc(100%-273px)] border-t-2 overflow-auto">
                <div class="pt-2"></div>
                <div v-if="false" class="text-center mt-6 text-xl text-gray-500">
                    No comments...
                </div>

                <div v-else class="flex items-center justify-between px-8 mt-4">
                    <div class="flex items-center relative w-full">
                        <NuxtLink href="/">
                            <img class="absolute top-0 rounded-full lg:mx=0 mx-auto" width="40"
                                src="https://p3-passport.byteimg.com/img/user-avatar/8b29c46c806762d72e9cb19a43b490dd~100x100.image"
                                alt="">
                        </NuxtLink>
                        <div class="ml-14 pt-0.5 w-full">
                            <div class="text-[18px] font-semibold flex items-center justify-between">
                                User name
                                <Icon v-if="true" @click="deleteComment" class="cursor-pointer"
                                    name="material-symbols:delete-outline-sharp" size="25" />
                            </div>
                            <div class="text-[15px] font-light">
                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Ratione voluptatem, similique
                                corporis incidunt eos accusantium tempora omnis a odit corrupti commodi laborum
                                exercitationem quidem beatae explicabo nemo facilis numquam repudiandae?
                            </div>
                        </div>
                    </div>
                </div>
                <div class="mb-28"></div>
            </div>

            <!-- 评论输入 -->
            <div id="CreateComment" v-if="true"
                class="absolute flex items-center justify-between bottom-0 bg-white h-[85px] lg:max-w-[550px] w-full py-5 px-8 border-t-2 ">

                <div :class="inputFocused ? 'border-2 border-gray-400' : 'border-2 border-[#f1f1f2]'"
                    class="bg-[#f1f1f2] flex items-center rounded-lg w-full lg:max-w-[420px]">
                    <input type="text" v-model="comment" @focus="inputFocused = true" @blur="inputFocused = false"
                        class="bg-[#f1f1f2] text-[14px] focus:outline-none w-full lg:max-w-[420px] p-2 rounded-lg"
                        placeholder="Add a comment...">
                </div>

                <button :disabled="!comment" @click="addComment"
                    :class="comment ? 'text-[#f02c56] cursor-pointer' : 'text-gray-400 cursor-not-allowed'"
                    class="font-semibold text-sm ml-5 pr-1">Post</button>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">

const route = useRoute()
const router = useRouter()

const video = ref<HTMLVideoElement>()

const isLoaded = ref(false)
const inputFocused = ref(false)
const comment = ref('')

// 向上
const loopThroughPostUp = () => { }

// 向下
const loopThroughPostDown = () => { }

// 删除视频
const deletePost = () => { }

// 删除评论
const deleteComment = () => { }

// 发评论
const addComment = () => { }

watch(() => isLoaded.value, (newV) => {
    if (newV) {
        setTimeout(() => {
            video.value!.play()
        }, 200)
    }
})

onMounted(() => {
    if (video.value) {
        video.value.addEventListener('loadeddata', (e: Event) => {
            if (e.target) {
                setTimeout(() => {
                    isLoaded.value = true
                }, 200)
            }
        })
    }
})

onBeforeUnmount(() => {
    video.value!.pause();
    video.value!.currentTime = 0;
    video.value!.src = '';
})
</script> 