<template>
  <div class="bg-green-500 h-screen">
    <div class="container mx-auto p-2">
      <div
        class="my-20 rounded-lg shadow-xl max-w-sm mx-auto bg-white px-5 py-10"
      >
        <h3 class="mb-8 text-center text-green-700">Mixvoip</h3>
        <form>
          <div class="w-full">
            <video ref="videoRef" autoplay="true" />
          </div>
          <div>
            <label ref="">Video source: </label>
            <select v-model="videoSelect"></select>
          </div>
          <div>
            <label ref="">Audio source: </label>
            <select v-model="videoSelect"></select>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const videoRef = ref("");
    const audioSelect = ref("");
    const videoSelect = ref("");

    if (navigator.mediaDevices.getUserMedia) {
      navigator.mediaDevices.getUserMedia({ video: true }).then((stream) => {
        videoRef.value.srcObject = stream;
      });
    }

    navigator.mediaDevices
      .enumerateDevices()
      .then(function (devices) {
        devices.forEach(function (device) {
          console.log(
            device.kind + ": " + device.label + " id = " + device.deviceId
          );
        });
      })
      .catch(function (err) {
        console.log(err.name + ": " + err.message);
      });

    return { videoRef, audioSelect, videoSelect };
  },
};
</script>


<style>
</style>
