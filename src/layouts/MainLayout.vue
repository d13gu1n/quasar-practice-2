<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          no-caps
          dense
          label="Probá"
          @click="testMethods"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <WSLJamboard :test-label="testLabel" :api-test="apiTest"/>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import WSLJamboard from 'components/WSLJamboard.vue'
import { axiosApi } from "src/boot/axios.js"

const testLabel = ref("");
const apiTest = ref({})

async function testMethods () {
  console.log("It works!! 😊");
  testLabel.value = "This is, indeed, doing it's job 😍";
  console.log("🚀 ~ testLabel:", testLabel.value);
  apiTest.value = await getTestAPIData();
  console.log("Axios is working?? ---> ", apiTest.value);
}

function getTestAPIData () {
  return axiosApi.get("testPropMessage").then(res => res.data);
}
</script>
