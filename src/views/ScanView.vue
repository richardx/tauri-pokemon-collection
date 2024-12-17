<template>
  <div class="scan-view">
    <!-- Kamera Preview -->
    <div v-if="cameraActive" class="camera-preview">
      <video ref="videoElement" autoplay playsinline></video>
    </div>

    <!-- Kontrolknapper -->
    <div class="buttons">
      <button @click="startCamera">Start Kamera</button>
      <button @click="stopCamera">Luk Kamera</button>
    </div>
  </div>
</template>

<script setup>
  import { onBeforeUnmount, ref } from 'vue';

  const cameraActive = ref(false);
  const videoElement = ref(null);
  let mediaStream = null;

  const startCamera = async () => {
    if (!cameraActive.value) {
      try {
        mediaStream = await navigator.mediaDevices.getUserMedia({
          video: true,
        });
        videoElement.value.srcObject = mediaStream;
        cameraActive.value = true;
      } catch (error) {
        console.error('Fejl ved adgang til kamera:', error);
      }
    }
  };

  const stopCamera = () => {
    if (cameraActive.value && mediaStream) {
      mediaStream.getTracks().forEach((track) => track.stop());
      mediaStream = null;
      cameraActive.value = false;
    }
  };

  onBeforeUnmount(() => {
    stopCamera();
  });
</script>

<style scoped>
  .camera-preview {
    width: 100%;
    height: auto;
  }
  .buttons {
    margin-top: 10px;
  }
  button {
    margin-right: 10px;
    padding: 10px 20px;
  }
</style>
