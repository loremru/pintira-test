<script setup>
import VideoEditor from "./components/video-editor.vue";
import {ref} from "vue";

const editorRef = ref()
function onInput(e) {
  editorRef.value?.createVideoEditor(URL.createObjectURL(e.target.files[0]))
}
</script>

<template>
  <p>select file to open pintura</p>
  <input accept="video/*" type="file" @input="onInput" >


  <VideoEditor ref="editorRef"/>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
