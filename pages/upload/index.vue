<template>
    <UploadError :errorType="errorType" />
    <UploadLayout>
        <div class="w-full mt-[80px] mb-[40px] bg-white shadow-lg rounded-md py-6 md:px-10 px-4">
            <div>
                <div class="text-[23px] font-semibold">
                    Upload Video
                </div>
                <div class="text-gray-400 mt-1">
                    Post a video to your account
                </div>
            </div>
            <div class="mt-8 md:flex gap-6">
                <!-- upload video -->
                <label v-if="!fileDisplay" @drop.prevent="onDrop" @dragover.prevent=""
                    class="md:mx-0 mx-auto mt-4 mb-6 flex flex-col items-center justify-center w-full max-w-[260px] h-[470px] text-center p-3 border-2 border-dashed border-gray-300 rounded-lg hover:bg-gray-100 cursor-pointer drop-shadow-2xl"
                    for="fileInput">
                    <Icon name="majesticons:cloud-upload" color="b3b3b1" size="40" />
                    <div class="mt-4 text-[17px]">Select video to upload</div>
                    <div class="mt-1.5 text-gray-500 text-[13px]">Or drag and grop a file</div>
                    <div class="mt-12 text-gray-400 text-sm">MP4</div>
                    <div class="mt-2 text-gray-400 text-[13px]">Up to 30 minutes</div>
                    <div class="mt-2 text-gray-400 text-[13px]">Less than 2 GB</div>
                    <div class="px-2 py-1.5 mt-8 text-white text-[15px] w-[80%] bg-[#F02C56] rounded-sm">
                        Select File
                    </div>
                    <input ref="file" id="fileInput" hidden accept=".mp4" @change="onChange" type="file">
                </label>

                <!-- show video -->
                <div v-else
                    class="md:mx-0 mx-auto mt-4 md:mb-12 mb-16 flex items-center justify-center w-full max-w-[260px] h-[540px] p-3 rounded-xl cursor-pointer relative">
                    <div class="bg-black h-full w-full">
                    </div>

                    <img class="absolute z-20 pointer-events-none" src="~/assets/images/mobile-case.png">
                    <img class="absolute right-4 bottom-6 z-20" width="90" src="~/assets/images/tiktok-logo-white.png">
                    <video autoplay loop muted class="absolute rounded-xl object-cover z-10 p-[13px] w-full h-full"
                        :src="fileDisplay"></video>

                    <div
                        class="absolute -bottom-12 flex items-center justify-between z-50 rounded-xl border w-full p-2 border-gray-300">
                        <div class="flex items-center truncate">
                            <Icon class="min-w-[16px]" name="clarity:success-standard-line" color="" size="16" />
                            <div class="text-[11px] pl-1 truncate text-ellipsis">{{ fileData.name }}</div>
                        </div>
                        <button class="text-[11px] ml-2 font-semibold" @click="clearVideo">Change</button>
                    </div>
                </div>

                <div class="mt-4 mb-6">
                    <!-- Edit button -->
                    <div class="flex bg-[#F8F8F8] py-4 px-6">
                        <div>
                            <Icon class="mr-4" name="mdi:box-cutter-off" color="" size="20" />
                        </div>
                        <div>
                            <div class="text-semibold text-[15px] mb-1.5">Divide videos and edit</div>
                            <div class="text-semibold text-[13px] text-gray-400">
                                You can quickly divide videos into multiple parts.
                                remove redundant parts and turn landspace videos into portrait videos
                            </div>
                        </div>
                        <div class="flex justify-end max-w-[130px] w-full h-full text-center my-auto">
                            <button class="px-8 py-1.5 text-white text-[15px] bg-[#F02C56] rounded-sm">Edit</button>
                        </div>
                    </div>

                    <!-- form & btn -->
                    <div class="mt-5">
                        <div class="flex items-center justify-between">
                            <div class="mb-1 text-[15px]">Caption</div>
                            <div class="text-gray-400 text-[12px]">{{ caption.length }}/150</div>
                        </div>
                        <input class="w-full border p-2.5 rounded-md focus:outline-none" type="text" maxlength="150"
                            v-model="caption">
                    </div>
                    <div class="flex gap-3">
                        <button class="px-10 py-2.5 mt-8 border text-[16px] hover:bg-gray-100 rounded-md"
                            @click="discard">Discard</button>
                        <button
                            class="px-10 py-2.5 mt-8 border text-[16px] text-white bg-[#F02C56] rounded-md">Post</button>
                    </div>
                </div>
            </div>
        </div>
    </UploadLayout>
</template>

<script setup lang="ts">
import UploadLayout from '~/layouts/UploadLayout.vue'

const file = ref()
const fileDisplay = ref()
const errorType = ref<string>('')
const caption = ref<string>('')
const fileData = ref()
const errors = ref()
const isUploading = ref<boolean>(false)


watch(() => caption.value, (caption) => {
    if (caption.length >= 150) {
        errorType.value = 'caption'
        return
    }
    errorType.value = ''
})

// 拖拽上传
const onDrop = (e: any) => {
    errorType.value = ''
    file.value = e.dataTransfer.files[0]
    fileData.value = e.dataTransfer.files[0]

    let extension = file.value.name.substring(file.value.name.lastIndexOf('.') + 1)

    if (extension !== 'mp4') {
        errorType.value = 'file'
        return
    }
    fileDisplay.value = URL.createObjectURL(e.dataTransfer.files[0])
}

// 点击上传
const onChange = () => {
    fileDisplay.value = URL.createObjectURL(file.value.files[0])
    fileData.value = file.value.files[0]
}

// discard btn
const discard = () => {
    file.value = null
    fileData.value = null
    fileDisplay.value = false
    caption.value = ''
}

// change btn
const clearVideo = () => {
    file.value = null
    fileDisplay.value = null
    fileData.value = null
}
</script>