<template>
    <div class="w-[100%] relative flex justify-center">
        <div class="absolute top-6 z-50 mx-auto bg-black bg-opacity-70 text-white px-14 py-3 rounded-md"
            :class="errorType ? 'visible' : 'invisible'">
            {{ error }}
        </div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{ errorType: string }>()

const error = ref<string>('')

interface errorsI {
    caption: string
    bio: string
    file: string
}
const errors: errorsI = {
    caption: 'Maximum 150 characters',
    bio: 'Maximum 150 characters',
    file: 'Unsupported file. Use mp4 instead.',
}
type errorsType = keyof errorsI // 'caption' | 'bio' | 'file'

watch(() => props.errorType, (newV: string) => {
    error.value = errors[newV as errorsType]
})
</script>
