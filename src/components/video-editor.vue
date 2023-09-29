<template>
  <div></div>
</template>

<script setup>
import { ref } from 'vue'
import { setPlugins, openDefaultEditor, imageStateToCanvas } from '@pqina/pintura'
import '@pqina/pintura/pintura.css'

import {
  createDefaultVideoWriter,
  createFFmpegEncoder,
  plugin_trim,
  plugin_trim_locale_en_gb,
} from '@pqina/pintura-video'
import '@pqina/pintura-video/pinturavideo.css'

setPlugins(plugin_trim)
const emit = defineEmits(['edit'])
const modalRef = ref()

function createVideoEditor(src) {
  modalRef.value = openDefaultEditor({
    src,
    locale: {
      ...plugin_trim_locale_en_gb,
    },
    imageMaxDuration: 180,
    imageWriter: createDefaultVideoWriter({
      // Use FFmpeg encoder
      encoder: createFFmpegEncoder({
        imageStateToCanvas,
        scriptPath: '/ffmpeg/ffmpeg.js',
        corePath: '/ffmpeg/core/ffmpeg-core.js',
        log: true,
      }),
    }),
  })
}

defineExpose({
  createVideoEditor,
})
</script>

<style scoped></style>
