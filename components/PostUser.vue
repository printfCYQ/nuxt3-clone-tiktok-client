<template>
    <div @mouseenter="isHover(true)" @mouseleave="isHover(false)"
        class="relative brightness-90 hover:brightness-[1.1] cursor-pointer">
        <div v-if="!isLoaded"
            class="absolute flex items-center justify-center top-0 left-0 aspect-[3/4] w-full object-cover rounded-md bg-black">
            <Icon class="animate-spin ml-1" name="mingcute:loading-line" color="#ffffff" size="100" />
        </div>

        <div>
            <video ref="video" muted loop class="aspect-[3/4] object-cover rounded-md" src="/test.mp4"></video>
        </div>

        <div class="px-1">
            <div class="text-gray-700 text-[15px] pt-1 break-words">
                This is some text

            </div>
            <div class="flex items-center -ml-1 text-gray-600 font-bold text-xs">
                <Icon name="gg:loadbar-sound" size="20" />
                3%
                <Icon class="ml-1" name="tabler:alert-circle" size="16" />
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">

const route = useRoute()
const router = useRouter()

const video = ref<HTMLVideoElement>()
const isLoaded = ref<boolean>(false)

defineProps(['post'])

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
const isHover = (value: boolean) => {
    value ? video.value?.play() : video.value?.pause()
}
</script>
