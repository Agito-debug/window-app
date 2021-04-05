<template>
  <div class="bg-green-600 h-full">
    <div class="container mx-auto p-1">
      <div
        class="my-20 rounded-xl shadow-xl max-w-sm mx-auto bg-white px-5 py-10"
      >
        <h3 class="mb-8 text-center text-green-700">Mixvoip</h3>
        <form>
          <div class="w-full">
            <video class="rounded-2xl" ref="videoRef" autoplay="true" />
          </div>

          <div>
            <label ref="">Video source: </label>
            <svg
              class="w-5 absolute mt-2.5 ml-1.5"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                d="M2 6a2 2 0 012-2h6a2 2 0 012 2v8a2 2 0 01-2 2H4a2 2 0 01-2-2V6zM14.553 7.106A1 1 0 0014 8v4a1 1 0 00.553.894l2 1A1 1 0 0018 13V7a1 1 0 00-1.447-.894l-2 1z"
              />
            </svg>
            <select
              class="w-full border border-gray-300 px-3 py-2 rounded-lg shadow-sm focus:outline-none focus:border-green-500 focus:ring-0"
              v-model="videoSelect"
            ></select>
          </div>
          <div>
            <label ref="">Audio source: </label>
            <svg
              class="w-5 absolute mt-2.5 ml-1.5"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                fill-rule="evenodd"
                d="M7 4a3 3 0 016 0v4a3 3 0 11-6 0V4zm4 10.93A7.001 7.001 0 0017 8a1 1 0 10-2 0A5 5 0 015 8a1 1 0 00-2 0 7.001 7.001 0 006 6.93V17H6a1 1 0 100 2h8a1 1 0 100-2h-3v-2.07z"
                clip-rule="evenodd"
              />
            </svg>
            <select
              class="w-full border border-gray-300 px-3 py-2 rounded-lg shadow-sm focus:outline-none focus:border-green-500 focus:ring-0"
              v-model="videoSelect"
            ></select>
          </div>
          <div>
            <label ref="">Audio source: </label>
            <svg
              class="w-5 absolute mt-2.5 ml-1.5"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                fill-rule="evenodd"
                d="M9.383 3.076A1 1 0 0110 4v12a1 1 0 01-1.707.707L4.586 13H2a1 1 0 01-1-1V8a1 1 0 011-1h2.586l3.707-3.707a1 1 0 011.09-.217zM14.657 2.929a1 1 0 011.414 0A9.972 9.972 0 0119 10a9.972 9.972 0 01-2.929 7.071 1 1 0 01-1.414-1.414A7.971 7.971 0 0017 10c0-2.21-.894-4.208-2.343-5.657a1 1 0 010-1.414zm-2.829 2.828a1 1 0 011.415 0A5.983 5.983 0 0115 10a5.984 5.984 0 01-1.757 4.243 1 1 0 01-1.415-1.415A3.984 3.984 0 0013 10a3.983 3.983 0 00-1.172-2.828 1 1 0 010-1.415z"
                clip-rule="evenodd"
              />
            </svg>
            <select
              class="w-full border border-gray-300 px-3 py-2 rounded-lg shadow-sm focus:outline-none focus:border-green-500 focus:ring-0"
              v-model="videoSelect"
            ></select>
          </div>

          <button
            class="w-full mt-8 bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-full"
          >
            Join Meeting
          </button>
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

    if (navigator.mediaDevices.getUserMedia) {
      navigator.mediaDevices.getUserMedia({ video: true }).then((stream) => {
        videoRef.value.srcObject = stream;
      });
    }

    (async function allDevices() {
      await navigator.mediaDevices.getUserMedia({ audio: true, video: true });
      let devices = await navigator.mediaDevices.enumerateDevices();
      return devices;
    })();

    return { videoRef };
  },
};
</script>


<style>
</style>
