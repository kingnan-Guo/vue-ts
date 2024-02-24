<template>
    <div class="about">
      <h1>This is an about page</h1>
      <HelloWorld msg="123"/>
    </div>
  </template>
  
  <script lang="ts" setup>
import { computed, reactive } from "vue";

    
    const data = reactive({one: 1, two: "n"})
    data.OT = computed(() => {
        return data.one + data.two
    })
  
  </script>


